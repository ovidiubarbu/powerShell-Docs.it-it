---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,sicurezza
title: Controllo e creazione di report in JEA
ms.openlocfilehash: 60bc7a4213c75735628207bb21078bf90f7b1ca3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="auditing-and-reporting-on-jea"></a>Controllo e creazione di report in JEA

> Si applica a: Windows PowerShell 5.0

Dopo aver distribuito JEA, è possibile controllarne regolarmente la configurazione.
Ciò consentirà di valutare se gli utenti corretti hanno accesso all'endpoint JEA e se i loro ruoli assegnati sono ancora appropriati.

Questo argomento descrive i vari modi con cui è possibile controllare un endpoint JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Trovare le sessioni JEA registrate in un computer

Per controllare quali sessioni JEA sono registrate in un computer, usare il cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Le autorizzazioni effettive per l'endpoint sono elencate nella proprietà "Permission".
Questi utenti hanno il diritto di connettersi all'endpoint JEA, ma i ruoli (e, di conseguenza, i comandi) a cui hanno accesso sono determinati dal campo "RoleDefinitions" nel [file di configurazione sessione](session-configurations.md) usato per registrare l'endpoint.

È possibile valutare i mapping dei ruoli in un endpoint JEA registrato espandendo i dati nella proprietà "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Trovare le funzionalità di ruolo disponibili nel computer

I file delle funzionalità del ruolo verranno usati da JEA solo se sono archiviati in una cartella "RoleCapabilities" all'interno di un modulo di PowerShell valido.
È possibile trovare tutte le funzionalità di ruolo disponibili in un computer eseguendo una ricerca nell'elenco dei moduli disponibili.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> L'ordine dei risultati di questa funzione non è necessariamente l'ordine in cui verranno selezionate le funzionalità di ruolo se più funzionalità di ruolo condividono lo stesso nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Controllare le autorizzazioni effettive per un utente specifico

Dopo aver impostato un endpoint JEA, è possibile verificare quali comandi sono disponibili per un utente specifico in una sessione JEA.
È possibile usare [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) per enumerare tutti i comandi applicabili a utenti se devono avviare una sessione JEA con l'appartenenza al gruppo corrente.
L'output di `Get-PSSessionCapability` è identico a quello dell'utente specificato che esegue `Get-Command -CommandType All` in una sessione JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se gli utenti non sono membri permanenti di gruppi che concedono diritti JEA aggiuntivi, questo cmdlet potrebbe non tenere in considerazione le autorizzazioni aggiuntive.
Ciò avviene in genere quando si usano sistemi di gestione di accesso con privilegi just-in-time (JIT) per consentire agli utenti di far temporaneamente parte di un gruppo di sicurezza.
Valutare sempre il mapping degli utenti ai ruoli e il contenuto di ogni ruolo per assicurarsi che gli utenti ottengano accesso solo al numero minimo di comandi necessari per svolgere il proprio lavoro.

## <a name="powershell-event-logs"></a>Log eventi di PowerShell

Se è stata abilitata la registrazione blocco di script e/o moduli nel sistema, sarà possibile trovare gli eventi nei log eventi Windows per ogni comando eseguito nelle sessioni JEA.
Per trovare questi eventi, aprire il Visualizzatore eventi di Windows, passare al log eventi **Microsoft-Windows-PowerShell/Operational** e cercare gli eventi con ID evento **4104**.

Ogni voce del log eventi include informazioni sulla sessione in cui è stato eseguito il comando.
Per le sessioni JEA, la voce include informazioni importanti su **ConnectedUser**, che corrisponde all'utente che ha creato la sessione JEA, e su **RunAsUser**, che identifica l'account JEA usato per eseguire il comando.
I log eventi dell'applicazione includono le modifiche eseguite da RunAsUser, pertanto è molto importante abilitare la registrazione di moduli/script per poter tracciare una chiamata al comando specifico di un utente.

## <a name="application-event-logs"></a>Log eventi dell'applicazione

Quando si esegue un comando in una sessione JEA che interagisce con applicazioni esterne o con un servizio, tali applicazioni potrebbero registrare eventi nei propri log eventi.
Diversamente dalle trascrizioni e dai log di PowerShell, gli altri meccanismi di registrazione non memorizzano l'utente connesso alla sessione JEA e registrano invece solo l'utente virtuale RunAs o l'account del servizio gestito del gruppo.
Per determinare l'utente che ha eseguito il comando, è necessario vedere una [trascrizione di sessione](#session-transcripts) o correlare i log eventi di PowerShell con l'ora e l'utente indicato nel log eventi dell'applicazione.

Il log di WinRM consente anche di correlare utenti RunAs in un log eventi dell'applicazione con l'utente che si connette.
L'ID evento **193** nel log **Microsoft-Windows-Windows Remote Management/Operational** registra l'ID di sicurezza (SID) e il nome account dell'utente che si connette e dell'utente RunAs, ogni volta che viene creata una sessione JEA.

## <a name="session-transcripts"></a>Trascrizioni di sessione

Se è stato configurato JEA per creare una trascrizione per ogni sessione utente, una copia in formato testo di tutte le azioni dell'utente verrà archiviata nella cartella specificata.

Per trovare tutte le directory di trascrizione, eseguire il comando seguente con privilegi di amministratore nel computer configurato con JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Ogni trascrizione inizia con informazioni sul tempo di avvio della sessione, sull'utente connesso alla sessione e sull'identità JEA assegnata.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Nel corpo della trascrizione, vengono registrate informazioni su ogni comando chiamato dall'utente.
La sintassi esatta del comando che è stato eseguito dall'utente non è disponibile nelle sessioni JEA a causa del modo in cui i comandi vengono trasformati per la comunicazione remota di PowerShell, comunque è sempre possibile determinare il comando eseguito.
Di seguito viene illustrato un frammento di trascrizione di esempio da un utente che esegue `Get-Service Dns` in una sessione JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Per ogni comando eseguito da un utente, viene scritta una riga "CommandInvocation", che descrive il cmdlet o la funzione chiamata dall'utente.
ParameterBindings segue ogni CommandInvocation per specificare informazioni su ogni parametro e valore usato con il comando.
Nell'esempio precedente, è possibile notare che nel parametro "Name" è stato specificato il valore "Dns" per il cmdlet "Get-Service".

L'output di ogni comando genera anche un CommandInvocation, in genere per Out-Default. InputObject di Out-Default è l'oggetto PowerShell restituito dal comando.
I dettagli di tale oggetto vengono aggiunti in alcune righe di sotto, emulando strettamente ciò che avrebbe visto l'utente.

## <a name="see-also"></a>Vedere anche

- [Controllare le azioni dell'utente in una sessione JEA](audit-and-report.md)
- [Post di blog sulla sicurezza di *PowerShell ♥ the Blue Team*](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

