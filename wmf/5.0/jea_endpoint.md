---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 66db78cfb136f22cad9078d7113dad085ee667a5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188429"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Creazione e connessione a un endpoint JEA
Per creare un endpoint JEA, è necessario creare e registrare un file di configurazione di sessione di PowerShell appositamente configurato, che può essere generato con il cmdlet **New-PSSessionConfigurationFile**.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Questo comando creerà un file di configurazione di sessione simile al seguente:
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

}
```
Quando si crea un endpoint JEA, è necessario impostare i seguenti parametri del comando (e le chiavi corrispondenti nel file):
1.  SessionType su RestrictedRemoteServer
2.  RunAsVirtualAccount su **$true**
3.  TranscriptPath sulla directory in cui verranno salvate le trascrizioni "Over The Shoulder" dopo ogni sessione
4.  RoleDefinitions su una tabella hash che definisce quali gruppi hanno accesso a quali "capacità del ruolo".  Questo campo definisce **chi** può fare **cosa** su questo endpoint.   Le capacità del ruolo sono file speciali che verranno spiegati più avanti.


Il campo RoleDefinitions definisce quali gruppi hanno avuto accesso a quali capacità del ruolo.  Con capacità del ruolo si intende un file che definisce un set di capacità che verranno esposte per gli utenti che si connettono.  È possibile creare capacità del ruolo con il comando **New PSRoleCapabilityFile**.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Verrà generato un file di capacità del ruolo modello simile al seguente:
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}

```
Per poterle usare in una configurazione di sessione JEA, le capacità del ruolo devono essere salvate come modulo di PowerShell valido in una directory denominata "RoleCapabilities". Per un modulo possono esistere più file di capacità del ruolo, se necessario.

Per iniziare a configurare i cmdlet, le funzioni, gli alias e gli script a cui può accedere un utente durante la connessione a una sessione JEA, aggiungere regole personalizzate nel file delle capacità del ruolo, come indicato nei modelli impostati come commento. Per informazioni più approfondite su come è possibile configurare le capacità del ruolo, vedere la [guida all'esperienza](http://aka.ms/JEA) completa.

Infine, dopo aver completato la personalizzazione della configurazione di sessione e delle capacità del ruolo correlate, registrare questa configurazione di sessione e creare l'endpoint eseguendo **Register-PSSessionConfiguration**.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Connettersi a un Endpoint JEA
La connessione a un Endpoint JEA funziona nello stesso modo della connessione a qualsiasi altro endpoint di PowerShell.  È sufficiente specificare il nome dell'endpoint JEA come parametro "ConfigurationName" per **New-PSSession**, **Invoke-Command** o **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
Dopo essersi connessi alla sessione JEA, sarà consentita solo l'esecuzione dei comandi inclusi tra le capacità del ruolo a cui si ha accesso. Se si tenta di eseguire qualsiasi comando non consentito per il ruolo, si verificherà un errore.
