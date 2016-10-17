# Update-Module

Scarica e installa la versione più recente dei moduli specificati da una raccolta online nel computer locale.

## Descrizione

Il cmdlet Update-Module consente di installare una versione più recente di un modulo di Windows PowerShell installato dalla raccolta online eseguendo Install-Module nel computer locale.

Per impostazione predefinita, viene installata la versione più recente del modulo specificato nella raccolta online, a meno che non sia specificata una versione richiesta. È possibile aggiornare un modulo esistente installato specificando il nome del modulo. Update-Module cerca $env:PSModulePath per il modulo da aggiornare.

L'esecuzione di Update-Module senza il parametro Name aggiorna tutti i moduli che possono essere aggiornati nel computer locale.

### Note

- Questo cmdlet viene eseguito in Windows PowerShell 3.0 o versioni successive di Windows PowerShell, in Windows 7 o Windows 2008 R2 e nelle versioni successive di Windows.
- Se il modulo specificato con il parametro Name non è stato installato con Install-Module, si verifica un errore. È possibile eseguire Update-Module solo nei moduli installati dalla raccolta online eseguendo Install-Module.
- Se Update-Module prova ad aggiornare i file binari in uso, restituisce un errore che identifica i processi che causano il problema e indica all'utente di rieseguire Update-Module dopo l'arresto dei processi.
- In PowerShell 5.0 o versioni successive, quando Update-Module aggiorna un modulo, aggiunge la versione più recente o quella specificata del modulo, in modo che le versioni precedenti e più recenti siano visualizzate side-by-side nella stessa directory. Sarebbe utile avere un esempio dell'output di questi comandi.


## Sintassi del cmdlet
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## Riferimento per la Guida online sui cmdlet

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## Comandi di esempio

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  Aggiornare il modulo TestDepWithNestedRequiredModules1 con le dipendenze.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

<!--HONumber=Aug16_HO3-->


