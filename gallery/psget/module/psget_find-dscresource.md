# Find-DscResource

Trova le risorse DSC nei moduli.

## Descrizione

Il cmdlet Find--DscResource trova le risorse [DSC (Desired State Configuration)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) contenute nei moduli che corrispondono ai criteri specificati nei repository registrati.
Per ogni modulo trovato da questo cmdlet, Find-DscResource restituisce un oggetto PSGetDscResourceInfo che è possibile inviare tramite pipe a Install-Module per installare i moduli contenenti le risorse restituite da questo cmdlet.

DSC è una nuova piattaforma di gestione di Windows PowerShell che consente di distribuire e gestire dati di configurazione per i servizi software, nonché di gestire l'ambiente in cui vengono eseguiti questi servizi.

Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC. Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.

Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS. I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.

- Find-DscResource consente di filtrare usando i parametri di versione MinimumVersion, RequiredVersion e AllVersions.
  - Questi parametri si escludono a vicenda.
  - Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.
  - Se il parametro RequiredVersion non è specificato, Find-DscResource restituisce la versione più recente del modulo maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo.
  - Se il parametro RequiredVersion è specificato, Find-DscResource restituisce unicamente la versione del modulo che corrisponde esattamente alla versione specificata.
- Find-DscResource consente di filtrare in base ai metadati del modulo usando il parametro -Tag
- Find-DscResource consente di filtrare in base al linguaggio di ricerca specifico del repository usando il parametro -Filter.
- Find-DscResource consente di filtrare in base ai moduli di tutti o alcuni dei repository registrati.

## Sintassi del cmdlet
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## Riferimento per la Guida online sui cmdlet

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## Comandi di esempio
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```


<!--HONumber=Aug16_HO3-->


