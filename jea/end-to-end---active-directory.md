---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: end-to-end Active Directory
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0a262e2c83174db7041d3cf35d97542b1cac4386

---

# End-to-end - Active Directory
Si supponga che l'ambito del programma sia aumentato
e di essere responsabili dell'aggiunta di JEA ai controller di dominio per eseguire azioni di Active Directory.
Il personale dell'help desk userà JEA per sbloccare gli account, reimpostare le password ed eseguire altre operazioni simili.

È necessario esporre un set di comandi completamente nuovo per un altro gruppo di persone.
In più, si dovrà esporre anche una serie di script di Active Directory già esistenti.
In questa sezione verrà illustrata la creazione di una configurazione di sessione e delle capacità del ruolo per questa attività.

## Prerequisiti
Per seguire le istruzioni dettagliate di questa sezione, è necessario lavorare su un controller di dominio.
Se non si ha accesso al proprio controller di dominio non è un problema.
Provare a seguire la procedura lavorando in un altro scenario o ruolo con cui si ha familiarità.
Per configurare rapidamente un nuovo controller di dominio, consultare l'appendice [Creazione di un controller di dominio](#creating-a-domain-controller).

## Procedura per la creazione di una nuova capacità del ruolo e una configurazione di sessione

Creare una nuova capacità del ruolo può essere scoraggiante all'inizio, ma l'operazione può essere suddivisa in passaggi abbastanza semplici:

1.  Identificare le attività che è necessario abilitare
2.  Limitare le attività secondo le esigenze
3.  Verificare che funzionino con JEA
4.  Inserirle in un file di capacità del ruolo
5.  Registrare una configurazione di sessione che espone la capacità del ruolo

## Passaggio 1: Identificare gli elementi da esporre
Prima di creare una nuova capacità del ruolo o configurazione di sessione, è necessario identificare tutte le attività che gli utenti dovranno svolgere attraverso l'endpoint JEA, nonché le modalità di gestione con PowerShell.
Questo comporta un discreto lavoro di ricerca e raccolta dei requisiti.
Il modo di procedere dipende dall'organizzazione e dagli obiettivi.
È importante sottolineare che la ricerca e la raccolta dei requisiti costituiscono una parte essenziale del processo reale.
Potrebbe trattarsi del passaggio più difficile del processo di adozione di JEA.

### Reperire le risorse
Di seguito sono riportate alcune risorse online che potrebbero apparire nella ricerca in relazione alla creazione di un endpoint di gestione di Active Directory:
-   [Panoramica di Active Directory PowerShell](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [Guida per il passaggio da CMD a PowerShell per Active Directory](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### Creare un elenco
Ecco una serie di dieci azioni che verranno usate più avanti in questa sezione.
Tenere presente che si tratta semplicemente di un esempio, i requisiti della propria organizzazione possono essere diversi:

|Azione                                                         |Comando di PowerShell                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|Sblocco dell'account                                                 |`Unlock-ADAccount`                                             |
|Reimpostazione della password                                                 |`Set-ADAccountPassword` e `Set-ADUser -ChangePasswordAtLogon`|
|Modifica del titolo di un utente                                          |`Set-ADUser -Title`                                            |  
|Ricerca di account di Active Directory bloccati, disabilitati, inattivi e così via |`Search-ADAccount`                                             |
|Aggiunta di un utente a un gruppo                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|Rimozione di un utente da un gruppo                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|Abilitazione di un account utente                                          |`Enable-ADAccount`                                             |
|Disabilitazione di un account utente                                         |`Disable-ADAccount`                                            |

## Passaggio 2: Limitare le attività secondo le esigenze

Ora che si ha a disposizione un elenco di azioni, è necessario valutare la funzionalità di ogni comando.
Esistono due motivi principali per eseguire questa operazione:

1.  È facile esporre più funzionalità del previsto per gli utenti.
Ad esempio, `Set-ADUser` è un comando incredibilmente potente e flessibile.
È opportuno evitare di esporre tutto ciò che è in grado di fare agli utenti dell'help desk.  

2.  Peggio ancora, è possibile esporre comandi che consentono agli utenti di evitare le restrizioni di JEA.
In questo caso JEA smette di funzionare come limite di sicurezza.
Prestare attenzione quando si selezionano i comandi.
Ad esempio, Invoke-Expression consentirà agli utenti di eseguire codice senza restrizioni.
Per altre informazioni su questo argomento, vedere la sezione relativa alla limitazione dei comandi.

Dopo aver esaminato ogni comando, si decide di limitare quanto segue:

1.  `Set-ADUser` deve essere eseguito solo con il parametro "-Title"

2.  `Add-ADGroupMember` e `Remove-ADGroupMember` deve funzionare solo con alcuni gruppi

### Passaggio 3: Verificare se le attività funzionano con JEA
Usare i cmdlet potrebbe non essere semplice nell'ambiente JEA con restrizioni.
JEA viene eseguito in modalità *NoLanguage* che, tra l'altro, impedisce agli utenti di usare le variabili.
Per garantire che gli utenti finali usufruiscano di un'esperienza ottimale, è importante verificare alcuni aspetti.

Ad esempio, considerare `Set-ADAccountPassword`.
Il parametro "-NewPassword" richiede una stringa sicura.
Spesso gli utenti creano un stringa sicura e la passano come variabile, come indicato di seguito:

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

La modalità NoLanguage impedisce l'uso delle variabili.
È possibile aggirare questa restrizione in due modi:

1.  È possibile richiedere agli utenti di eseguire il comando senza assegnare variabili.
La relativa configurazione è semplice, ma può diventare macchinosa per gli operatori che usano l'endpoint,
che ad ogni reimpostazione di una password dovrebbero digitare quanto segue:
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  È possibile ridurre la complessità usando uno script o una funzione da esporre agli utenti finali.
Le funzioni e gli script esposti vengono eseguiti in un contesto senza restrizioni. È possibile scrivere funzioni che usano le variabili e chiamano altri comandi senza alcun problema.
Questo approccio semplifica l'esperienza dell'utente finale, impedisce gli errori, riduce la competenza necessaria con PowerShell ed evita che vengano esposte involontariamente funzionalità in eccesso.
L'unico svantaggio è costituito dai costi di creazione e gestione della funzione.

### Approfondimento: Aggiunta di una funzione al modulo
Con l'approccio n. 2 si scrive una funzione di PowerShell denominata `Reset-ContosoUserPassword`.
Questa funzione dovrà eseguire tutte le operazioni necessarie quando si reimposta la password di un utente.
In un'organizzazione questo può significare dover svolgere attività elaborate e complesse.
Poiché si tratta semplicemente di un esempio, il comando si limiterà a reimpostare la password e a richiedere all'utente di cambiare la password all'accesso.
Il comando verrà inserito nel modulo Contoso_AD_Module creato nell'ultima sezione.

1. In PowerShell ISE aprire "Contoso_AD_Module.psm1"
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. Premere CTRL + J per aprire il menu dei frammenti di codice.

3. Premere la freccia in basso finché non appare "function" e premere INVIO.
In questo modo viene creato uno "scheletro" molto essenziale di funzione.

4. Rinominare la funzione "Reset-ContosoUserPassword".  

5. Rinominare uno dei parametri "Identity" ed eliminare il secondo.

6. Copiare quanto segue nel corpo della funzione.
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. Salvare il file.
Il risultato dovrebbe essere simile al seguente:
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
A questo punto, gli utenti possono semplicemente chiamare `Reset-ContosoUserPassword` senza dover ricordare la sintassi richiesta per creare una stringa sicura inline.

## Passaggio 4: Modificare il file di capacità del ruolo
Nella sezione [Creazione di capacità del ruolo](#role-capability-creation) è stato creato un file di capacità del ruolo vuoto.
In questa sezione verranno inseriti i valori nel file.

Per prima cosa, aprire il file di capacità del ruolo in ISE.
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
Aggiornare il file con le seguenti modifiche:
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

Riguardo al codice riportato sopra è necessario osservare quanto segue:
1.  PowerShell tenterà di caricare automaticamente i moduli necessari per la capacità del ruolo.
Può essere necessario indicare in modo esplicito i nomi dei moduli nel campo "ModulesToImport" se si riscontrano problemi con un modulo che non viene caricato automaticamente.

2.  Per verificare se un comando è un cmdlet o una funzione, eseguire `Get-Command` e controllare "CommandType"

3.  ValidatePattern consente di usare un'espressione regolare per limitare gli argomenti di parametro, nel caso in cui non sia facile definire un set di valori consentiti.
Non è possibile definire sia un valore ValidatePattern che un valore ValidateSet per un singolo parametro.

## Passaggio 5: Registrare una nuova configurazione di sessione
È necessario creare un nuovo file di configurazione di sessione che esporrà la capacità del ruolo ai membri del gruppo "JEA_NonAdmin_HelpDesk" di Active Directory.

Per iniziare, creare e aprire un nuovo file di configurazione di sessione vuoto in PowerShell ISE.
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
Modificare i campi seguenti nel file PSSC.
Se si lavora nel proprio ambiente, è necessario sostituire "CONTOSO\JEA_NonAdmins_Helpdesk" con il proprio utente o gruppo non amministratore.
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for active directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
Salvare e registrare la configurazione di sessione
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## Testare la configurazione
Ottenere le credenziali di utente non amministratore:
```PowerShell
$HelpDeskCred = Get-Credential
```
Se si è seguita la sezione [Configurare utenti e gruppi](creating-a-domain-controller.md#set-up-users-and-groups) le credenziali sono:
-   Username = "HelpDeskUser"
-   Password = "pa$$w0rd"

Accedere in remoto all'endpoint dell'help desk di Active Directory usando le credenziali di utente non amministratore:
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
Usare Set-ADUser per reimpostare il titolo di un utente.
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
Verificare che il titolo è stato modificato.
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
A questo punto, usare Add-ADGroupMember per aggiungere un utente al gruppo TestGroup.
Nota: verificare che TestGroup sia già stato creato.
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
Chiudere la sessione:
```PowerShell
Exit-PSSession
```
## Concetti chiave
**Modalità NoLanguage**: quando PowerShell è in modalità "NoLanguage", gli utenti possono solo eseguire i comandi e non possono usare elementi del linguaggio.
Per altre informazioni, eseguire `Get-Help about_Language_Modes`.

**Funzioni di PowerShell**: le funzioni di PowerShell sono parti di codice di PowerShell che è possibile chiamare in base al nome.
Per altre informazioni, eseguire `Get-Help about_Functions`.

**ValidateSet/ValidatePattern**: quando si espone un comando, è possibile limitare gli argomenti validi per parametri specifici.
ValidateSet indica un elenco specifico di comandi validi.
ValidatePattern è un'espressione regolare a cui gli argomenti per il parametro devono corrispondere.




<!--HONumber=Jun16_HO4-->


