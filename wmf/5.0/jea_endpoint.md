---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: c3645a6ba83081bd5ac31a13af0f67f6538db22a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="18c13-102">Creazione e connessione a un endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="18c13-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="18c13-103">Per creare un endpoint JEA, è necessario creare e registrare un file di configurazione di sessione di PowerShell appositamente configurato, che può essere generato con il cmdlet **New-PSSessionConfigurationFile**.</span><span class="sxs-lookup"><span data-stu-id="18c13-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

<span data-ttu-id="18c13-104">Questo comando creerà un file di configurazione di sessione simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="18c13-104">This will create a session configuration file that looks like this:</span></span> 
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
<span data-ttu-id="18c13-105">Quando si crea un endpoint JEA, è necessario impostare i seguenti parametri del comando (e le chiavi corrispondenti nel file):</span><span class="sxs-lookup"><span data-stu-id="18c13-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="18c13-106">SessionType su RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="18c13-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="18c13-107">RunAsVirtualAccount su **$true**</span><span class="sxs-lookup"><span data-stu-id="18c13-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="18c13-108">TranscriptPath sulla directory in cui verranno salvate le trascrizioni "Over The Shoulder" dopo ogni sessione</span><span class="sxs-lookup"><span data-stu-id="18c13-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="18c13-109">RoleDefinitions su una tabella hash che definisce quali gruppi hanno accesso a quali "capacità del ruolo".</span><span class="sxs-lookup"><span data-stu-id="18c13-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="18c13-110">Questo campo definisce **chi** può fare **cosa** su questo endpoint.</span><span class="sxs-lookup"><span data-stu-id="18c13-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="18c13-111">Le capacità del ruolo sono file speciali che verranno spiegati più avanti.</span><span class="sxs-lookup"><span data-stu-id="18c13-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="18c13-112">Il campo RoleDefinitions definisce quali gruppi hanno avuto accesso a quali capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="18c13-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="18c13-113">Con capacità del ruolo si intende un file che definisce un set di capacità che verranno esposte per gli utenti che si connettono.</span><span class="sxs-lookup"><span data-stu-id="18c13-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="18c13-114">È possibile creare capacità del ruolo con il comando **New PSRoleCapabilityFile**.</span><span class="sxs-lookup"><span data-stu-id="18c13-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

<span data-ttu-id="18c13-115">Verrà generato un file di capacità del ruolo modello simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="18c13-115">This will generate a template role capability that looks like this:</span></span>
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
<span data-ttu-id="18c13-116">Per poterle usare in una configurazione di sessione JEA, le capacità del ruolo devono essere salvate come modulo di PowerShell valido in una directory denominata "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="18c13-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="18c13-117">Per un modulo possono esistere più file di capacità del ruolo, se necessario.</span><span class="sxs-lookup"><span data-stu-id="18c13-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="18c13-118">Per iniziare a configurare i cmdlet, le funzioni, gli alias e gli script a cui può accedere un utente durante la connessione a una sessione JEA, aggiungere regole personalizzate nel file delle capacità del ruolo, come indicato nei modelli impostati come commento.</span><span class="sxs-lookup"><span data-stu-id="18c13-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="18c13-119">Per informazioni più approfondite su come è possibile configurare le capacità del ruolo, vedere la [guida all'esperienza](http://aka.ms/JEA) completa.</span><span class="sxs-lookup"><span data-stu-id="18c13-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="18c13-120">Infine, dopo aver completato la personalizzazione della configurazione di sessione e delle capacità del ruolo correlate, registrare questa configurazione di sessione e creare l'endpoint eseguendo **Register-PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="18c13-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="18c13-121">Connettersi a un Endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="18c13-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="18c13-122">La connessione a un Endpoint JEA funziona nello stesso modo della connessione a qualsiasi altro endpoint di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="18c13-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="18c13-123">È sufficiente specificare il nome dell'endpoint JEA come parametro "ConfigurationName" per **New-PSSession**, **Invoke-Command** o **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="18c13-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="18c13-124">Dopo essersi connessi alla sessione JEA, sarà consentita solo l'esecuzione dei comandi inclusi tra le capacità del ruolo a cui si ha accesso.</span><span class="sxs-lookup"><span data-stu-id="18c13-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="18c13-125">Se si tenta di eseguire qualsiasi comando non consentito per il ruolo, si verificherà un errore.</span><span class="sxs-lookup"><span data-stu-id="18c13-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>

