# Moduli con versioni di PowerShell compatibili
A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

- **Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.
- **Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.

## L'edizione di PowerShell in esecuzione viene visualizzata nella proprietà PSEdition di $PSVersionTable.
```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## Gli autori di moduli possono dichiarare i propri moduli compatibili con una o più edizioni di PowerShell usando la chiave manifesto del modulo CompatiblePSEditions. Questa chiave è supportata solo in PowerShell 5.1 o versioni successive.
*Nota* Quando un manifesto del modulo è stato specificato con la chiave CompatiblePSEditions, non può più essere importato in versioni di PowerShell precedenti.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$moduleInfo = Test-ModuleManifest -Path \TestModuleWithEdition.psd1
$moduleInfo.CompatiblePSEditions
Desktop
Core

$moduleInfo | Get-Member CompatiblePSEditions

   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}

```
Quando si recupera un elenco dei moduli disponibili, è possibile filtrarlo in base all'edizione di PowerShell.
```powershell
Get-Module -ListAvailable -PSEdition Desktop

    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions

Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
Desktop
Core

```

## Gli autori dei moduli possono pubblicare un modulo singolo di destinazione a una o entrambe le edizioni di PowerShell (Desktop e Core) 

Un modulo singolo può essere usato sia nell'edizione Desktop che nell'edizione Core purché l'autore vi aggiunga la logica necessaria in RootModule o nel manifesto del modulo usando la variabile $PSEdition.
I moduli possono avere due set di DLL compilate con destinazione sia CoreCLR che FullCLR.
Di seguito sono riportate le due opzioni per creare il pacchetto del modulo con la logica per il caricamento delle DLL appropriate.

### Opzione 1: creazione di un modulo destinabile a più versioni e più edizioni di PowerShell

#### Contenuto della cartella del modulo

 Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll Microsoft.Windows.PowerShell.ScriptAnalyzer.dll PSScriptAnalyzer.psd1 PSScriptAnalyzer.psm1 ScriptAnalyzer.format.ps1xml ScriptAnalyzer.types.ps1xml coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll en-US\about_PSScriptAnalyzer.help.txt en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll Settings\CmdletDesign.psd1 Settings\DSC.psd1 Settings\ScriptFunctions.psd1 Settings\ScriptingStyle.psd1 Settings\ScriptSecurity.psd1

#### Contenuto del file PSScriptAnalyzer.psd1

```powershell
@{
 
# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### Contenuto del file PSScriptAnalyzer.psm1
La logica riportata qui sotto carica gli assembly necessari in base all'edizione o alla versione corrente.

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }    
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
} 

```

### Opzione 2: uso della variabile $PSEdition nel file PSD1 per caricare le DLL appropriate e moduli nidificati/richiesti

Nella versione PS 5.1 o successiva la variabile globale $PSEdition è consentita nel file manifesto del modulo.
Usando questa variabile l'autore del modulo può specificare i valori condizionali nel file manifesto del modulo. È possibile fare riferimento alla variabile $PSEdition in modalità linguaggio con restrizioni o in una sezione di dati. 

*Nota* Quando un manifesto del modulo è stato specificato con la chiave CompatiblePSEditions oppure usa la variabile $PSEdition, non può più essere importato in versioni di PowerShell precedenti.


#### Esempio di file manifesto del modulo con la chiave CompatiblePSEditions

```powershell
@{ 
# - - -
 
# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}
 
# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'
 
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}
 
# -- - -
}
```

#### Contenuto del modulo

```powershell

PS C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions> dir -Recurse
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
d-----         7/5/2016   1:37 PM                clr                                                                                 
d-----         7/5/2016   1:36 PM                coreclr                                                                             
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1                                                             
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl                                                                      
 
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr
 
Mode                LastWriteTime         Length Name                                                                                
----                -------------         ------ ----                                                                                
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll                                                                    
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl                                                                      
```

## Gli utenti della raccolta di PowerShell possono visualizzare l'elenco dei moduli supportati in un'edizione specifica di PowerShell usando i tag PSEdition_Desktop e PSEditon_Core.
I moduli senza tag PSEdition_Desktop e PSEditon_Core sono considerati idonei per le edizioni Desktop di PowerShell.

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEditon_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEditon_Core

```


## Altri dettagli
### [Script con PSEditions](../script/scriptwithpseditionsupport.md)
### [Supporto di PSEditions nella raccolta di PowerShell](../../psgallery/psgallery_pseditions.md)


<!--HONumber=Aug16_HO5-->


