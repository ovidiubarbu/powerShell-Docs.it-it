---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: Scrittura di moduli portabili
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682552"
---
# <a name="portable-modules"></a>Moduli portatili

È stata scritta per Windows PowerShell [.NET Framework][] anche se è stata scritta per PowerShell Core [.NET Core][]. I moduli portatili sono moduli che funzionano in Windows PowerShell e PowerShell Core. Anche se .NET Framework e .NET Core sono estremamente compatibili, esistono differenze tra le due API disponibili. Esistono anche differenze nelle API disponibile in Windows PowerShell e PowerShell Core. Può essere utilizzato in entrambi gli ambienti di moduli devono essere a conoscenza di queste differenze.

## <a name="porting-an-existing-module"></a>Porting di un modulo esistente

### <a name="porting-a-pssnapin"></a>Porting di un PSSnapIn

PowerShell SnapIns (PSSnapIn) non sono supportate in PowerShell Core. Tuttavia, è semplice per convertire un PSSnapIn a un modulo di PowerShell. In genere, il codice di registrazione PSSnapIn è in un singolo file di origine di una classe che deriva da [PSSnapIn][]. Rimuovere il file di origine della compilazione; non è più necessario.

Uso [New-ModuleManifest][] per creare un nuovo manifesto del modulo che sostituisce la necessità per il codice di registrazione PSSnapIn. Alcuni dei valori di PSSnapIn (ad esempio descrizione) può essere riutilizzata nel manifesto del modulo.

Il `RootModule` proprietà nel manifesto del modulo deve essere impostata sul nome dell'assembly (dll) che implementa i cmdlet.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET Portability Analyzer (APIPort aka)

Ai moduli porta scritti per Windows PowerShell per lavorare con PowerShell Core, iniziare con il [.NET Portability Analyzer][]. Eseguire questo strumento per l'assembly compilato per determinare se le API .NET usato nel modulo sono compatibili con .NET Framework, .NET Core e altri Runtime .NET. Lo strumento consiglia API alternative se presenti. In caso contrario, potrebbe essere necessario aggiungere [controlli di runtime][] e limitare la funzionalità non disponibili nei runtime specifici.

## <a name="creating-a-new-module"></a>Creare un nuovo modulo

Se si crea un nuovo modulo, è consigliabile usare la [INTERFACCIA CLI DI .NET][].

### <a name="installing-the-powershell-standard-module-template"></a>Installazione del modello di modulo di PowerShell Standard

Dopo aver installata l'interfaccia CLI di .NET, installare una libreria di modelli per generare un semplice modulo di PowerShell.
Il modulo potrà essere compatibile con Windows PowerShell, PowerShell Core, Windows, Linux e macOS.

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

### <a name="creating-a-new-module-project"></a>Crea un nuovo progetto di modulo

Dopo aver installato il modello, è possibile creare un nuovo progetto di modulo di PowerShell utilizzando tale modello. In questo esempio, il modulo di esempio viene chiamato 'myModule'.

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

### <a name="building-the-module"></a>Creazione del modulo

Usare i comandi della CLI di .NET standard per compilare il progetto.

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

Dopo aver compilato il modulo, è possibile importarlo ed eseguire il cmdlet di esempio.

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

## <a name="net-standard-library"></a>Libreria .NET standard

[.NET standard][] è una specifica formale delle API .NET che sono disponibili in tutte le implementazioni .NET. Gestito codice destinato a .NET Standard funziona con le versioni di .NET Framework e .NET Core che sono compatibili con tale versione di .NET Standard.

> [!NOTE]
> Anche se può esistere un'API in .NET Standard, l'implementazione di API in .NET Core può generare un `PlatformNotSupportedException` in fase di esecuzione, pertanto, per verificare la compatibilità con Windows PowerShell e PowerShell Core, la procedura consigliata consiste nell'eseguire i test per il modulo all'interno di entrambi gli ambienti.
> Anche eseguire test in Linux e macOS, se il modulo deve essere multipiattaforma.

Scelta di .NET Standard consente di garantire che, come il modulo si evolve, le API incompatibili non ottenere introdotti accidentalmente nel modulo. Problemi di incompatibilità vengono individuati in fase di compilazione invece di runtime.

Tuttavia, non è necessario alla destinazione .NET Standard per un modulo per lavorare con Windows PowerShell e PowerShell Core, purché si utilizzino API compatibili. Il linguaggio intermedio (IL) è compatibile tra i due Runtime. È possibile scegliere .NET Framework 4.6.1, che è compatibile con .NET Standard 2.0. Se non si usano le API di fuori di .NET Standard 2.0, quindi il modulo funziona con PowerShell Core 6 senza ricompilazione.

## <a name="powershell-standard-library"></a>Libreria Standard di PowerShell

Il [PowerShell Standard][] libreria è una specifica formale delle APIs PowerShell disponibili in tutte le versioni di PowerShell maggiore o uguale alla versione di tale standard.

Ad esempio, [PowerShell Standard 5.1][] è compatibile con Windows PowerShell 5.1 e PowerShell Core 6.0 o versioni successive.

È consigliabile che si compila il modulo usando la libreria Standard di PowerShell. La libreria garantisce che le API sono disponibili e implementate in Windows PowerShell e PowerShell Core 6.
Standard di PowerShell deve sempre essere compatibile con l'inoltro. Un modulo compilato utilizzando PowerShell 5.1 libreria Standard saranno sempre compatibile con le versioni future di PowerShell.

## <a name="module-manifest"></a>Manifesto del modulo

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Che indica la compatibilità con Windows PowerShell e PowerShell Core

Dopo aver verificato che il modulo funziona con Windows PowerShell e PowerShell Core, il manifesto del modulo deve indicare in modo esplicito la compatibilità con le [CompatiblePSEditions][] proprietà. Un valore pari `Desktop` significa che il modulo è compatibile con Windows PowerShell, mentre un valore di `Core` significa che il modulo è compatibile con PowerShell Core. Inclusi i `Desktop` e `Core` significa che il modulo è compatibile con Windows PowerShell e PowerShell Core.

> [!NOTE]
> `Core` non significa che il modulo è compatibile con Windows, Linux e macOS.
> Il **CompatiblePSEditions** proprietà è stato introdotto in PowerShell versione 5. Modulo manifesti che utilizzano le **CompatiblePSEditions** caricamento nelle versioni precedenti a PowerShell versione 5 proprietà ha esito negativo.

### <a name="indicating-os-compatibility"></a>Che indica la compatibilità del sistema operativo

Per prima cosa, verificare che il modulo di funzioni in Linux e macOS. Successivamente, indicano la compatibilità con il sistema operativo nel manifesto del modulo. Questo rende più semplice agli utenti di trovare un modulo per il proprio sistema operativo quando pubblicato per la [PowerShell Gallery][].

Nel manifesto del modulo, il `PrivateData` proprietà ha un `PSData` sottoproprietà. L'opzione facoltativa `Tags` proprietà di `PSData` accetta una matrice di valori che vengono visualizzati in PowerShell Gallery. PowerShell Gallery supporta i seguenti valori di compatibilità:

| Tag               | Description                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatibile con PowerShell Core 6          |
| PSEdition_Desktop | Compatibile con Windows PowerShell         |
| Windows           | Compatibile con Windows                    |
| Linux             | Compatibile con Linux (Nessuna distribuzione specifica) |
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
[INTERFACCIA CLI DI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
