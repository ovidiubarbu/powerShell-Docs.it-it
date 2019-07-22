---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Controllo e creazione di report in JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726750"
---
# <a name="auditing-and-reporting-on-jea"></a>Controllo e creazione di report in JEA

Dopo aver distribuito JEA, è necessario controllarne regolarmente la configurazione. Ciò consente di valutare se gli utenti corretti hanno accesso all'endpoint JEA e se i loro ruoli assegnati sono ancora appropriati.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Trovare le sessioni JEA registrate in un computer

Per controllare quali sessioni JEA sono registrate in un computer, usare il cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Le autorizzazioni effettive per l'endpoint sono elencate nella proprietà **Permission**. Questi utenti hanno il diritto di connettersi all'endpoint JEA. I ruoli e, di conseguenza, i comandi a cui hanno accesso sono tuttavia determinati dalla proprietà **RoleDefinitions** nel [file di configurazione sessione](session-configurations.md) usato per registrare l'endpoint. Espandere la proprietà **RoleDefinitions** per valutare i mapping dei ruoli in un endpoint JEA registrato.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Trovare le funzionalità di ruolo disponibili nel computer

JEA ottiene le funzionalità del ruolo dai file `.psrc` archiviati nella cartella **RoleCapabilities** all'interno di un modulo di PowerShell. La funzione seguente consente di trovare tutte le funzionalità del ruolo disponibili in un computer.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> L'ordine dei risultati di questa funzione non è necessariamente l'ordine in cui verranno selezionate le funzionalità di ruolo se più funzionalità di ruolo condividono lo stesso nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Controllare le autorizzazioni effettive per un utente specifico

Il cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) enumera tutti i comandi disponibili in un endpoint JEA in base alle appartenenze ai gruppi di un utente.
L'output di `Get-PSSessionCapability` è identico a quello dell'utente specificato che esegue `Get-Command -CommandType All` in una sessione JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se gli utenti non sono membri permanenti di gruppi che concedono diritti JEA aggiuntivi, questo cmdlet potrebbe non tenere in considerazione le autorizzazioni aggiuntive. Ciò avviene quando si usano sistemi di gestione di accesso con privilegi just-in-time (JIT) per consentire agli utenti di far temporaneamente parte di un gruppo di sicurezza. Valutare con attenzione il mapping degli utenti ai ruoli e alle funzionalità per fare in modo che gli utenti ottengano solo il livello di accesso necessario per svolgere correttamente il proprio lavoro.

## <a name="powershell-event-logs"></a>Log eventi di PowerShell

Se è stata abilitata la registrazione blocco di script o moduli nel sistema, sarà possibile individuare gli eventi nei log eventi Windows per ogni comando eseguito in una sessione JEA. Per trovare questi eventi, aprire il log eventi **Microsoft-Windows-PowerShell/Operational** e cercare gli eventi con ID evento **4104**.

Ogni voce del log eventi include informazioni sulla sessione in cui è stato eseguito il comando. Per le sessioni JEA, l'evento include informazioni su **ConnectedUser** e **RunAsUser**. **ConnectedUser** è l'utente effettivo che ha creato la sessione JEA. **RunAsUser** è l'account JEA usato per eseguire il comando.

Nei log eventi dell'applicazione vengono visualizzate le modifiche apportate da **RunAsUser**. È quindi necessario abilitare la registrazione di moduli e script per poter tracciare una chiamata al comando specifico di **ConnectedUser**.

## <a name="application-event-logs"></a>Log eventi dell'applicazione

I comandi eseguiti in una sessione JEA che interagiscono con applicazioni o servizi esterni potrebbero registrare eventi nei propri log eventi. A differenza dei log e delle trascrizioni di PowerShell, gli altri meccanismi di registrazione non memorizzano l'utente connesso alla sessione JEA. Tali applicazioni registrano invece solo l'utente virtuale RunAs.
Per determinare l'utente che ha eseguito il comando, è necessario vedere una [trascrizione di sessione](#session-transcripts) o correlare i log eventi di PowerShell con l'ora e l'utente indicato nel log eventi dell'applicazione.

Il log di WinRM consente anche di correlare utenti RunAs con l'utente che si connette in un log eventi dell'applicazione. L'ID evento **193** nel log **Microsoft-Windows-Windows Remote Management/Operational** registra l'ID di sicurezza (SID) e il nome account dell'utente che si connette e dell'utente RunAs per ogni nuova sessione JEA.

## <a name="session-transcripts"></a>Trascrizioni di sessione

Se è stato configurato JEA per creare una trascrizione per ogni sessione utente, una copia in formato testo di tutte le azioni dell'utente verrà archiviata nella cartella specificata.

Il comando seguente (come amministratore) consente di trovare tutte le directory di trascrizione.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
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

Il corpo della trascrizione contiene informazioni su ogni comando chiamato dall'utente. La sintassi esatta del comando usato non è disponibile nelle sessioni JEA a causa del modo in cui i comandi vengono trasformati per la comunicazione remota di PowerShell. È tuttavia possibile determinare il comando effettivo che è stato eseguito. Di seguito viene illustrato un frammento di trascrizione di esempio da un utente che esegue `Get-Service Dns` in una sessione JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Viene scritta una riga **CommandInvocation** per ogni comando eseguito da un utente. **ParameterBindings** registra ogni parametro e valore specificato con il comando. Nell'esempio precedente si può osservare che nel parametro **Name** è stato specificato il valore **Dns** per il cmdlet `Get-Service`.

L'output di ogni comando genera anche un **CommandInvocation**, in genere per `Out-Default`. **InputObject** di `Out-Default` è l'oggetto PowerShell restituito dal comando. I dettagli di tale oggetto vengono aggiunti in alcune righe di sotto, emulando strettamente ciò che avrebbe visto l'utente.

## <a name="see-also"></a>Vedere anche

[Post di blog sulla sicurezza di *PowerShell ♥ the Blue Team*](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
