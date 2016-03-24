# Supporto delle versioni side-by-side in PowerShell 5.0 o versione successiva

I cmdlet Install-Module, Update-Module e Publish-Module eseguiti in Windows PowerShell 5.0 o versione successiva supportano ora versioni del modulo side-by-side (SxS).
È stato inoltre aggiunto il parametro -RequiredVersion al cmdlet Publish-Module per specificare la versione da pubblicare. Il parametro Path supporta ora il percorso di base del modulo con la cartella della versione.

**Esempi di Install-Module:**
```powershell
PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Type       Repository           Description            
-------    ----                                ----       ----------           -----------            
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
<!--HONumber=Mar16_HO2-->
