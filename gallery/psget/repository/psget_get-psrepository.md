# Get-PSRepository

Ottiene i repository registrati in un computer.

## Descrizione

Il cmdlet Get-PSRepository ottiene i repository del modulo di PowerShell registrati per l'utente corrente in un computer.

Per ogni repository registrato, Get-PSRepository restituisce un oggetto PSRepository che facoltativamente può essere inviato tramite pipe a Unregister-PSRepository per l'annullamento della registrazione di un repository registrato.

## Sintassi del cmdlet
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## Riferimento per la Guida online sui cmdlet

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## Comandi di esempio

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

<!--HONumber=Aug16_HO3-->


