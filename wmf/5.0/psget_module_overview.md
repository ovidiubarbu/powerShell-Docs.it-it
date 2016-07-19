# Individuazione, installazione e inventario dei moduli di PowerShell con PowerShellGet
 
PowerShellGet è incluso in questa versione di WMF:
-   Find-Module consente di filtrare in base ai metadati del modulo con il parametro -Tag
-   Find-Module consente di filtrare in base al linguaggio di ricerca specifico del repository con il parametro -Filter
-   Find-Module consente di filtrare in base al contenuto del modulo con i parametri -Command, -DscResource e -Includes
-   Find-DscResource consente l'individuazione delle singole risorse DSC nei repository
-   Supporto per l'installazione da e la pubblicazione in condivisioni file con NuGet

## Comandi di esempio
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## Nuove funzionalità di PowerShellGet
-   Supporto delle versioni side-by-side in Windows PowerShell 5.0 o versione successiva
-   Supporto dell'installazione delle dipendenze del modulo
-   Tre nuovi cmdlet
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
    

<!--HONumber=Jun16_HO4-->


