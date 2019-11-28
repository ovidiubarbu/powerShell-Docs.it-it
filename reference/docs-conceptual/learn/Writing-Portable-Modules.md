---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: Scrittura di moduli portabili
ms.openlocfilehash: 7871f524495c1ce5283b30696a24185d427edebf
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417635"
---
# <a name="portable-modules"></a>Moduli portabili

Windows PowerShell è scritto per [.NET Framework][], mentre PowerShell Core è scritto per [.NET Core][]. I moduli portabili sono compatibili con Windows PowerShell e PowerShell Core. Anche se .NET Framework e .NET Core sono estremamente compatibili, esistono differenze nelle API disponibili tra i due. Sussistono anche differenze nelle API disponibili in Windows PowerShell e PowerShell Core. I moduli destinati all'utilizzo in entrambi gli ambienti devono essere a conoscenza di queste differenze.

## <a name="porting-an-existing-module"></a>Porting di un modulo esistente

### <a name="porting-a-pssnapin"></a>Porting di uno snap-in PowerShell (PSSnapIn)

Gli [snap-in](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) PowerShell non sono supportati in PowerShell Core. Tuttavia, è semplice convertire uno snap-in a un modulo PowerShell. In genere, il codice di registrazione PSSnapIn si trova in un singolo file di origine di una classe derivata da [PSSnapIn][].
Rimuovere il file di origine dalla compilazione; non è più necessario.

Usare [New-ModuleManifest][] per creare un nuovo manifesto del modulo che rimuove la necessità del codice di registrazione PSSnapIn. Alcuni valori di **PSSnapIn** (ad esempio, **Description**) possono essere riutilizzati nel manifesto del modulo.

La proprietà **RootModule** nel manifesto del modulo deve essere impostata sul nome dell'assembly (dll) che implementa i cmdlet.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET Portability Analyzer (noto anche come APIPort)

Per eseguire il porting dei moduli scritti per Windows PowerShell e lavorare con PowerShell Core, iniziare con [.NET Portability Analyzer][]. Eseguire questo strumento sull'assembly compilato per determinare se le API .NET usate nel modulo sono compatibili con .NET Framework, .NET Core e altri runtime .NET. Lo strumento consiglia API alternative, se presenti. In caso contrario, potrebbe essere necessario aggiungere [controlli di runtime][] e limitare le funzionalità non disponibili nei runtime specifici.

## <a name="creating-a-new-module"></a>Creazione di un nuovo modulo

Se si crea un nuovo modulo, è consigliabile usare la [CLI .NET][].

### <a name="installing-the-powershell-standard-module-template"></a>Installazione del modello del modulo standard PowerShell

Dopo aver installato l'interfaccia della riga di comando di .NET, installare una libreria di modelli per generare un semplice modulo PowerShell.
Il modulo sarà compatibile con Windows PowerShell, PowerShell Core, Windows, Linux e macOS.

Nell'esempio seguente viene illustrato come installare il modello:

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Creazione di un nuovo progetto di modulo

Dopo aver installato il modello, sarà possibile usarlo per creare un nuovo progetto di modulo PowerShell. In questo esempio, il modulo campione viene chiamato 'myModule'.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>Compilazione del modulo

Usare i comandi standard dell'interfaccia della riga di comando di .NET per compilare il progetto.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>Test del modulo

Dopo aver compilato il modulo, sarà possibile importarlo ed eseguire il cmdlet campione.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

Le sezioni seguenti descrivono in dettaglio alcune delle tecnologie usate da questo modello.

## <a name="net-standard-library"></a>Libreria .NET Standard

[.NET standard][] è una specifica formale delle API .NET disponibili in tutte le implementazioni .NET. Il codice gestito destinato a .NET Standard funziona con le versioni di .NET Framework e .NET Core compatibili con tale versione di .NET Standard.

> [!NOTE]
> Sebbene possa essere presente un'API in .NET Standard, l'implementazione API in .NET Core può generare un'eccezione di tipo `PlatformNotSupportedException` in fase di esecuzione. Per verificare la compatibilità con Windows PowerShell e PowerShell Core, la procedura consigliata consiste nell'eseguire i test per il modulo all'interno di entrambi gli ambienti.
> Eseguire anche test in Linux e macOS, se il modulo deve essere multipiattaforma.

La scelta di .NET Standard come destinazione consente di garantire che, man mano che il modulo si evolve, non verranno introdotte accidentalmente API incompatibili nel modulo. Eventuali problemi di incompatibilità vengono individuati in fase di compilazione anziché in fase di esecuzione.

Tuttavia, non è necessario definire .NET Standard come destinazione per consentire a un modulo di funzionare con Windows PowerShell e PowerShell Core, purché si utilizzino API compatibili. Il linguaggio intermedio (IL) è compatibile tra i due runtime. È possibile indicare .NET Framework 4.6.1 come destinazione, compatibile con .NET Standard 2.0. Se non si usano API di fuori di .NET Standard 2.0, il modulo funziona con PowerShell Core 6 senza ricompilazione.

## <a name="powershell-standard-library"></a>Libreria di PowerShell Standard

La libreria di [PowerShell Standard][] è una specifica formale delle API PowerShell disponibili in tutte le versioni di PowerShell successive o uguali alla versione di Standard in uso.

Ad esempio, [PowerShell Standard 5.1][] è compatibile con Windows PowerShell 5.1 e PowerShell Core 6.0 o versioni successive.

È consigliabile compilare il modulo usando la libreria PowerShell Standard. La libreria garantisce che le API siano disponibili e vengano implementate in Windows PowerShell e PowerShell Core 6.
PowerShell Standard deve sempre essere compatibile con le versioni successive. Un modulo compilato utilizzando la libreria PowerShell Standard 5.1 sarà sempre compatibile con le versioni future di PowerShell.

## <a name="module-manifest"></a>Manifesto del modulo

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Indicazione di compatibilità con Windows PowerShell e PowerShell Core

Dopo aver verificato che il modulo funzioni con Windows PowerShell e PowerShell Core, il manifesto del modulo deve indicare in modo esplicito la compatibilità mediante la proprietà [CompatiblePSEditions][]. Il valore `Desktop` indica che il modulo è compatibile con Windows PowerShell, mentre il valore `Core` indica che il modulo è compatibile con PowerShell Core. Includendo `Desktop` e `Core`, il modulo è compatibile con Windows PowerShell e PowerShell Core.

> [!NOTE]
> `Core` non indica automaticamente che il modulo è compatibile con Windows, Linux e macOS.
> La proprietà **CompatiblePSEditions** è stata introdotto in PowerShell v5. I manifesti del modulo che usano la proprietà **CompatiblePSEditions** non vengono caricati nelle versioni precedenti a PowerShell v5.

### <a name="indicating-os-compatibility"></a>Indicazione di compatibilità con i sistemi operativi

Per prima cosa, verificare che il modulo funzioni in Linux e macOS. Successivamente, indicare la compatibilità con questi sistemi operativi nel manifesto del modulo. In questo modo è più semplice per gli utenti di trovare un modulo per il proprio sistema operativo in seguito alla pubblicazione in [PowerShell Gallery][].

Nel manifesto del modulo, la proprietà `PrivateData` ha una sottoproprietà `PSData`. La proprietà `Tags` facoltativa di `PSData` accetta una matrice di valori che vengono visualizzati in PowerShell Gallery. PowerShell Gallery supporta i valori di compatibilità seguenti:

| Tag               | Description                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatibili con PowerShell Core 6          |
| PSEdition_Desktop | Compatibile con Windows PowerShell         |
| Windows           | Compatibile con Windows                    |
| Linux             | Compatibile con Linux (nessuna distribuzione specifica) |
| macOS             | Compatibile con macOS                      |

Esempio:

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[controlli di runtime]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[CLI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
