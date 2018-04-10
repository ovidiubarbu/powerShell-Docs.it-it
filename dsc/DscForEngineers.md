---
ms.date: 10/13/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Panoramica di DSC (Desired State Configuration) per decision maker
ms.openlocfilehash: 3d2d4b7e09fb699751151d7af641410bae3b38a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Panoramica di DSC (Desired State Configuration) per tecnici

In questo documento è destinato ai team di sviluppatori e tecnici operativi per illustrare i vantaggi di PowerShell DSC (Desired State Configuration).
Per una panoramica di più alto livello del valore offerto da DSC, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](decisionMaker.md).

## <a name="benefits-of-desired-state-configuration"></a>Vantaggi dell'uso di DSC

DSC offre i vantaggi seguenti:

- Ridurre la complessità dello scripting in Windows
- Aumentare la velocità di iterazione

Il concetto di "distribuzione continua" è sempre più importante.
La distribuzione continua implica la possibilità di distribuire in modo frequente, potenzialmente più volte al giorno.
Lo scopo di queste distribuzioni non è quello di correggere un problema, ma di pubblicare funzionalità in tempi brevi.
Permettendo alle nuove funzionalità di passare dalla fase di sviluppo a quella operativa nel modo più rapido e affidabile possibile, si accelera il time-to-value della nuova logica di business.

La transizione verso il cloud computing implica una soluzione di distribuzione che utilizza un tipo di modello "dichiarativo", dove un ambiente di stato finale viene dichiarato come testo e pubblicato in un motore di distribuzione.
Questa tecnica di distribuzione consente cambiamenti rapidi su larga scala, con resilienza da rischi di errore perché in qualsiasi momento la distribuzione può essere ripetuta in modo coerente per garantire uno stato finale.
La creazione di strumenti e servizi che supportano questo tipo di operazioni tramite l'automazione è una risposta a queste modifiche.

DSC è una piattaforma che offre funzionalità di distribuzione, configurazione e conformità dichiarative e idempotenti (ripetibili).
La piattaforma DSC consente di verificare che i componenti del data center siano configurati correttamente, in modo da evitare errori e impedire costosi problemi di distribuzione.
Trattando le configurazioni DSC come parte del codice dell'applicazione, DSC consente la distribuzione continua.
La configurazione DSC deve essere aggiornata come parte dell'applicazione, assicurando così che le informazioni necessarie per distribuire l'applicazione siano sempre aggiornate e pronte per l'uso.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Se si ha PowerShell, perché è necessario usare anche Desired State Configuration?"

Le configurazioni DSC fanno distinzione tra l'intenzione, ossia "l'operazione che si vuole eseguire", e l'esecuzione, ossia "il modo in cui eseguire tale operazione".
Ciò significa che la logica di esecuzione è contenuta all'interno delle risorse.
Gli utenti non devono sapere come implementare o distribuire una funzionalità quando è disponibile una risorsa DSC per tale funzionalità.
In questo modo, gli utenti possono concentrarsi sulla struttura della loro distribuzione.

Ad esempio, gli script di PowerShell dovrebbero avere un aspetto simile al seguente:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Questo script è semplice e immediatamente comprensibile.
Se tuttavia si prova a trasferirlo nell'ambiente di produzione, possono verificarsi diversi problemi.
Cosa accade se lo script viene eseguito due volte di seguito?
E se un utente aveva l'accesso completo alla condivisione?

Per ovviare a questi problemi, una versione "reale" dello script avrà un aspetto più vicino al seguente:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Questo script è più complesso, con molte istruzioni per la gestione della logica e degli errori.
Lo script è più complesso perché non indica più le operazioni da eseguire, ma *in che modo eseguirle*.

DSC consente di specificare le operazioni da eseguire ed è in grado di astrarre la logica sottostante.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Questo script è formattato correttamente ed è facilmente leggibile.
I percorsi di logica e i criteri di gestione degli errori sono ancora presenti nell'implementazione della [risorsa](resources.md), ma non sono visibili all'autore dello script.

## <a name="separating-environment-from-structure"></a>Separazione dell'ambiente dalla struttura

Un modello comune in DevOps consiste nella presenza di più ambienti per la distribuzione.
Ad esempio, può essere presente un ambiente di sviluppo che consente di creare rapidamente prototipi di nuovo codice.
Il codice dell'ambiente di sviluppo viene trasferito in un ambiente di test, in cui altri utenti verificano la nuova funzionalità.
Infine, il codice passa all'ambiente di produzione, ossia all'ambiente del sito attivo.

Le configurazioni DSC supportano questa pipeline sviluppo-test-produzione tramite l'uso di [dati di configurazione](configData.md).
Questa caratteristica ha l'effetto di astrarre maggiormente la differenza tra la struttura della configurazione e i nodi gestiti.
È ad esempio possibile definire una configurazione che richiede un server SQL, un server IIS e un server di livello intermedio.
Indipendentemente dai nodi che ricevono le diverse parti della configurazione, questi tre elementi saranno sempre presenti.
È possibile usare i dati di configurazione per far puntare tutti e tre gli elementi allo stesso computer per un ambiente di sviluppo, separare i tre elementi su tre computer diversi per un ambiente di test e infine farli puntare a tutti i server di produzione per l'ambiente di produzione.
Per la distribuzione nei diversi ambienti, è possibile richiamare **Start-DscConfiguration** con i dati di configurazione corretti per l'ambiente di destinazione.

## <a name="see-also"></a>Vedere anche

[Configurazioni](configurations.md)

[Dati di configurazione](configData.md)

[Risorse](resources.md)