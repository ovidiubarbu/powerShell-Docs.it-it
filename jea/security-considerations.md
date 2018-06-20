---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Considerazioni sulla sicurezza in JEA
ms.openlocfilehash: 46ea5cc3e9bc7b6759524aa466e900950a6dee26
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190180"
---
# <a name="jea-security-considerations"></a>Considerazioni sulla sicurezza in JEA

> Si applica a: Windows PowerShell 5.0

JEA consente di migliorare le condizioni di sicurezza, riducendo il numero di amministratori permanenti nei computer.
Ciò avviene tramite la creazione per gli utenti di un nuovo punto di ingresso per gestire il sistema (con una configurazione sessione PowerShell) saldamente bloccato per impostazione predefinita per prevenire usi impropri.
Agli utenti che richiedono un accesso non illimitato al computer per eseguire attività amministrative è possibile concedere l'accesso all'endpoint JEA.
Poiché JEA consente di eseguire i comandi di amministratore senza avere accesso come amministratore, è quindi possibile rimuovere utenti da gruppi di sicurezza con privilegi elevati (renderli quindi utenti standard).

Questo argomento illustra in modo più dettagliato il modello di sicurezza in JEA e le procedure consigliate.

## <a name="run-as-account"></a>account RunAs

Ogni endpoint JEA ha un account designato "RunAs", ovvero l'account con cui vengono eseguite le azioni dall'utente che si connette.
Questo account è configurabile nel [file di configurazione sessione](session-configurations.md), e l'account scelto ha un impatto significativo sulla sicurezza dell'endpoint.

Il modo consigliato per configurare l'account RunAs è usare gli **account virtuali**.
Gli account virtuali sono account locali temporanei creati per l'utente che si connette e possono essere usati solo per la durata della sessione JEA.
Dopo aver terminato la sessione, l'account virtuale verrà eliminato e non può più essere usato.
L'utente che si connette non conosce le credenziali dell'account virtuale e non può usare l'account virtuale per accedere al sistema tramite altri mezzi, ad esempio Desktop remoto o un endpoint di PowerShell non vincolato.

Per impostazione predefinita, gli account virtuali appartengono al gruppo Administrators locale del computer.
Per questo motivo, hanno diritti completi per gestire qualsiasi elemento nel sistema, ma non possono gestire le risorse della rete.
Durante l'autenticazione con altri computer, il contesto utente sarà l'account del computer locale, non l'account virtuale.

I controller di dominio rappresentano un caso speciale, perché non esiste il concetto di gruppo di amministratori locali.
Gli account virtuali appartengono invece al gruppo Domain Admins e possono gestire i servizi directory nel controller di dominio.
L'identità di dominio è ancora limitata all'uso nel controller di dominio in cui è stata creata la sessione di JEA e qualsiasi accesso alla rete risulterà invece proveniente dall'oggetto computer del controller di dominio.

In entrambi i casi, è anche possibile definire in modo esplicito a quale gruppo di sicurezza deve appartenere l'account virtuale.
Questa è una procedura efficace se l'attività può essere eseguita senza privilegi di amministratore locale o di dominio.
Se è già disponibile un gruppo di sicurezza definito per gli amministratori, è possibile concedere l'appartenenza dell'account virtuale a tale gruppo per assegnare le autorizzazioni necessarie.
L'appartenenza al gruppo account virtuale è limitato a gruppi di sicurezza locali nella workstation e nei server membri, ma in un controller di dominio gli account virtuali possono essere solo membri di gruppi di sicurezza di dominio.
Quando si specificano uno o più gruppi di sicurezza, l'account virtuale non apparterrà più ai gruppi predefiniti (amministratore locale o di dominio).

La tabella seguente illustra le opzioni di configurazione possibili e le autorizzazioni risultanti per gli account virtuali

Tipo di computer                | Configurazione del gruppo di account virtuali | Contesto dell'utente locale                                      | Contesto dell'utente di rete
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Controller di dominio            | Default                             | Utente di dominio, membro di "*DOMAIN*\Domain Admins"         | Account del computer
Controller di dominio            | Gruppi di dominio A e B               | Utente di dominio, membro di "*DOMAIN*\A", "*DOMAIN*\B"       | Account del computer
Workstation o server membro | Default                             | Utente locale, membro di "*BUILTIN*\Administrators"        | Account del computer
Workstation o server membro | Gruppi locali C e D                | Utente locale, membro di "*COMPUTER*\C" e "*COMPUTER*\D" | Account del computer

Quando si esaminano gli eventi del controllo di sicurezza e i log eventi dell'applicazione, si noterà che ogni sessione utente JEA ha un account virtuale univoco.
Ciò consente di tenere traccia delle azioni dell'utente in un endpoint JEA all'utente originale che ha eseguito il comando.
I nome degli account virtuali seguono il formato "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*". Ad esempio, se l'utente "Alice" nel dominio "Contoso" riavvia un servizio in un endpoint JEA, il nome utente associato a eventi di gestione del controllo del servizio sarebbe "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice".


Gli **account del servizio gestito del gruppo (gMSAs)** sono utili quando un server membro ha bisogno di accedere alle risorse di rete nella sessione JEA.
Un caso d'uso di esempio è l'endpoint JEA usato per controllare l'accesso a un'API REST ospitata in un altro computer.
È semplice scrivere funzioni che creano le chiamate appropriate nell'API REST, ma per l'autenticazione con l'API è necessaria un'identità di rete.
L'uso di un account del servizio gestito del gruppo rende possibile il "secondo hop" mantenendo al contempo controllo sui computer che possono usare l'account.
Le autorizzazioni valide dei gMSA sono definite dai gruppi di sicurezza (locale o di dominio) a cui appartiene l'account gMSA.

Quando un endpoint JEA è configurato per usare un account gMSA, le azioni di tutti gli utenti JEA verranno registrate come se provenissero dallo stesso account del servizio gestito del gruppo.
L'unico modo possibile per tracciare le azioni per un utente specifico consiste nell'identificare il set di comandi eseguiti in una trascrizione della sessione di PowerShell.

Le **credenziali pass-through** vengono usate quando non si specifica un account RunAs e si vuole che PowerShell usi le credenziali dell'utente che si connette per eseguire i comandi nel server remoto.
Questa configurazione *non* è consigliata per JEA perché sarebbe necessario concedere all'utente che si connette l'accesso diretto ai gruppi di gestione con privilegi.
Se l'utente che si connette ha già privilegi di amministratore, è possibile evitare del tutto JEA e gestire il sistema con altri mezzi non vincolati.
Per altre informazioni, vedere la sezione seguente su come [JEA non protegge contro gli amministratori](#jea-does-not-protect-against-admins).

Gli **account RunAs standard** consentono di specificare qualsiasi account utente con cui verrà eseguita l'intera sessione di PowerShell.
Questa è una distinzione importante, perché una configurazione sessione impostata per l'uso di un account RunAs (con il parametro `-RunAsCredential`) non è compatibile con JEA.
Ciò significa che le definizioni di ruolo non funzionano più come previsto e a ogni utente autorizzato ad accedere all'endpoint verrà assegnato lo stesso ruolo.

È consigliabile non usare RunAsCredential su un endpoint JEA a causa della difficoltà di tracciare le azioni degli utenti specifici e della mancanza di supporto per eseguire il mapping degli utenti ai ruoli.

## <a name="winrm-endpoint-acl"></a>ACL endpoint di WinRM

Allo stesso modo degli endpoint regolari di comunicazione remota di PowerShell, ogni endpoint JEA ha un elenco di controllo di accesso (ACL) separato impostato nella configurazione WinRM, che controlla gli utenti che possono eseguire l'autenticazione con l'endpoint JEA.
Se la configurazione non è corretta, gli utenti attendibili potrebbero non essere in grado di accedere all'endpoint JEA e/o gli utenti non attendibili potrebbero ottenere accesso.
L'ACL WinRM non influisce tuttavia sul mapping degli utenti ai ruoli JEA.
Ciò viene controllato dal campo *RoleDefinitions* nel file di configurazione sessione registrato nel sistema.

Per impostazione predefinita, quando si registra un endpoint JEA usando un file di configurazione sessione e una o più funzionalità di ruolo, l'ACL WinRM verrà configurato per consentire il mapping di tutti gli utenti a uno o più ruoli per accedere all'endpoint.
Ad esempio, una sessione JEA configurata usando i comandi seguenti concederà accesso completo a *CONTOSO\JEA\_Lev1* e *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

È possibile controllare le autorizzazioni utente con il cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Per modificare l'accesso degli utenti, eseguire `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` per un prompt interattivo o `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` per aggiornare le autorizzazioni.
Gli utenti devono avere almeno i diritti di *chiamata* per accedere all'endpoint JEA.

Gli altri utenti che hanno accesso all'endpoint JEA ma non rientrano in nessuno ruolo definito nel file di configurazione sessione, saranno in grado di avviare una sessione JEA, ma avranno accesso solo ai cmdlet predefiniti.
È possibile controllare le autorizzazioni degli utenti in un endpoint JEA eseguendo `Get-PSSessionCapability`.
Vedere l'articolo [Controllo e creazione di report in JEA](audit-and-report.md) per altre informazioni sul controllo dei comandi ai quali ha accesso un utente in un endpoint JEA.

## <a name="least-privilege-roles"></a>Ruoli con privilegi minimi

Quando si progettano ruoli JEA, è importante ricordare che l'account virtuale o del servizio gestito del gruppo eseguito alla base ha spesso accesso illimitato per gestire il computer locale.
Le funzionalità del ruolo JEA limitano l'uso dell'account riducendo i comandi e le applicazioni che possono essere eseguite usando il contesto autorizzato.
I ruoli progettati in modo incorretto possono consentire l'esecuzione di comandi pericolosi che potrebbero portare un utente a oltrepassare i limiti JEA o ottenere accesso a informazioni riservate.

Ad esempio, prendere in considerazione la voce relativa alla funzionalità di ruolo seguente:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Questa funzionalità di ruolo consente agli utenti di eseguire qualsiasi cmdlet di PowerShell con il termine "Process" dal modulo Microsoft.PowerShell.Management.
Gli utenti possono aver bisogno di accedere a specifici cmdlet, ad esempio `Get-Process` per identificare le applicazioni in esecuzione nel sistema e `Stop-Process` per terminare qualsiasi applicazioni bloccata.
Questa voce consente anche il cmdlet `Start-Process`, che può essere usato per avviare un programma arbitrario con autorizzazioni complete di amministratore.
Il programma non deve essere installato localmente nel sistema, per cui un utente malintenzionato potrebbe avviare un programma in una condivisione di file che offre privilegi di amministratore locale all'utente che si connette, eseguire malware e così via.

Di seguito viene illustrata una versione più sicura della stessa funzionalità di ruolo:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evitare l'uso di caratteri jolly nelle funzionalità di ruolo e assicurarsi di [controllare le autorizzazioni utente effettive](audit-and-report.md#check-effective-rights-for-a-specific-user) regolarmente per sapere a quali comandi ha accesso un utente.

## <a name="jea-does-not-protect-against-admins"></a>JEA non offre protezione contro gli amministratori

Uno dei principi fondamentali di JEA è che consente a utenti non amministratori di eseguire *alcune* attività di amministrazione.
JEA non offre protezione contro gli utenti che hanno già privilegi di amministratore.
Gli utenti che appartengono ai gruppi "Domain Admins", "Amministratori locali" o ad altri gruppi con privilegi elevati saranno ancora in grado di aggirare le protezioni JEA accedendo al computer con altri mezzi.
Ad esempio, un utente potrebbe accedere con RDP, usare console MMC remote o connettersi agli endpoint di PowerShell non vincolati.
Gli amministratori locali del sistema possono anche modificare le configurazioni JEA per consentire ad altri utenti di gestire il sistema o modificare una funzionalità di ruolo per estendere l'ambito delle operazioni di ciò che un utente può eseguire nella sessione JEA.
È quindi importante valutare le autorizzazioni estese degli utenti JEA per verificare se ci sono altri modi con cui ottenere accesso privilegiato al sistema.

Una pratica comune è usare JEA per una regolare manutenzione quotidiana e avere una soluzione di gestione dell'accesso con privilegi "Just in Time" per consentire agli utenti di essere temporaneamente amministratori locali in situazioni di emergenza.
In questo modo gli utenti non saranno amministratori permanenti del sistema, ma possono ottenere tali diritti se e solo quando completano un flusso di lavoro che documenta l'uso di tali autorizzazioni.