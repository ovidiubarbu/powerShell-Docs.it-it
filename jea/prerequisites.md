---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: prerequisiti
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: ac9231a475ba84e9051bbd06a65f3f20c9e49846

---

# Prerequisiti

## Stato iniziale
Prima di iniziare questa sezione, verificare quanto segue:

1. JEA è disponibile nel sistema. Verificare nel file [README](./README.md) quali sono i sistemi operativi attualmente supportati e i download necessari.
2. Si dispone di diritti amministrativi nel computer in cui verrà usato JEA.
3. Il computer fa parte di un dominio.
Vedere la sezione [Creazione di un controller di dominio](#creating-a-domain-controller) per configurare rapidamente un nuovo dominio in un server se non ancora disponibile.

## Comunicazione remota di PowerShell
La gestione con JEA avviene attraverso la comunicazione remota di PowerShell.
Eseguire il comando seguente in una finestra di PowerShell come amministratore per verificare che la funzionalità sia abilitata e configurata correttamente:

```PowerShell
Enable-PSRemoting
```

Se non si ha familiarità con la comunicazione remota di PowerShell, è consigliabile eseguire `Get-Help about_Remote` per informazioni su questo concetto di fondamentale importanza.

## Identificare utenti o gruppi
Per visualizzare JEA in azione, è necessario identificare gli utenti e i gruppi non amministratori che si intende usare in questa guida.

Se si usa un dominio già esistente, identificare o creare alcuni gruppi e utenti senza privilegi.
Si concederà l'accesso a JEA a questi utenti non amministratori.
Ogni volta che viene visualizzata la variabile `$NonAdministrator` nella parte superiore di uno script, assegnarla ai propri utenti o gruppi non amministratori selezionati.

Se è stato creato un nuovo dominio da zero, è molto più semplice.
Usare la sezione [Configurare utenti e gruppi](creating-a-domain-controller.md#set-up-users-and-groups) dell'appendice per creare utenti e gruppi non amministratori.
I valori predefiniti di `$NonAdministrator` saranno i gruppi creati in tale sezione.

## Configurare il file di capacità del ruolo per la manutenzione
Eseguire i comandi seguenti in PowerShell per creare il file di capacità del ruolo dimostrativo che verrà usato nella sezione successiva.
Le operazioni eseguite dal file sono illustrate più avanti in questa guida.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions =
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams
```

## Creare e registrare un file di configurazione di sessione dimostrativo
Eseguire i comandi seguenti per creare e registrare un file dimostrativo della configurazione di sessione che verrà usato per la sezione successiva.
Le operazioni eseguite dal file sono illustrate più avanti in questa guida.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```

## Abilitare la registrazione per i moduli di PowerShell (facoltativo)
La procedura seguente consente di registrare tutte le azioni di PowerShell nel sistema.
Questa opzione non è necessaria per il funzionamento di JEA, ma risulterà utile nella sezione [Reporting on JEA](reporting-on-jea.md) (Creazione di report per JEA).

1. Aprire l'Editor criteri di gruppo locali
2. Passare a "Configurazione computer\Modelli amministrativi\Componenti di Windows\Windows PowerShell"
3. Fare doppio clic su "Attiva registrazione moduli"
4. Fare clic su "Abilitato".
5. Nella sezione Opzioni fare clic su "Mostra" accanto a Nomi moduli
6. Digitare "\*" nella finestra popup. Ciò significa che PowerShell registrerà i comandi da tutti i moduli.
7. Fare clic su OK e applicare i criteri

Nota: è possibile abilitare la trascrizione PowerShell a livello di sistema anche con i criteri di gruppo.

**Complimenti, il computer ora è configurato con l'endpoint dimostrativo ed è possibile iniziare a usare JEA.**




<!--HONumber=Aug16_HO3-->


