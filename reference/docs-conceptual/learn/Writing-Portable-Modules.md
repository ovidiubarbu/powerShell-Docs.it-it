---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: Scrittura di moduli portabili
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747722"
---
# <a name="portable-modules"></a><span data-ttu-id="40a7e-103">Moduli portatili</span><span class="sxs-lookup"><span data-stu-id="40a7e-103">Portable Modules</span></span>

<span data-ttu-id="40a7e-104">È stata scritta per Windows PowerShell [.NET Framework][] anche se è stata scritta per PowerShell Core [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="40a7e-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="40a7e-105">I moduli portatili sono moduli che funzionano in Windows PowerShell e PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="40a7e-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="40a7e-106">Anche se .NET Framework e .NET Core sono estremamente compatibili, esistono differenze tra le due API disponibili.</span><span class="sxs-lookup"><span data-stu-id="40a7e-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="40a7e-107">Esistono anche differenze nelle API disponibile in Windows PowerShell e PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="40a7e-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="40a7e-108">Può essere utilizzato in entrambi gli ambienti di moduli devono essere a conoscenza di queste differenze.</span><span class="sxs-lookup"><span data-stu-id="40a7e-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="40a7e-109">Porting di un modulo esistente</span><span class="sxs-lookup"><span data-stu-id="40a7e-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="40a7e-110">Porting di un PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="40a7e-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="40a7e-111">PowerShell SnapIns (PSSnapIn) non sono supportate in PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="40a7e-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="40a7e-112">Tuttavia, è semplice per convertire un PSSnapIn a un modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40a7e-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="40a7e-113">In genere, il codice di registrazione PSSnapIn è in un singolo file di origine di una classe che deriva da [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="40a7e-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="40a7e-114">Rimuovere il file di origine della compilazione; non è più necessario.</span><span class="sxs-lookup"><span data-stu-id="40a7e-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="40a7e-115">Uso [New-ModuleManifest][] per creare un nuovo manifesto del modulo che sostituisce la necessità per il codice di registrazione PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="40a7e-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="40a7e-116">Alcuni dei valori di PSSnapIn (ad esempio descrizione) può essere riutilizzata nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="40a7e-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="40a7e-117">Il `RootModule` proprietà nel manifesto del modulo deve essere impostata sul nome dell'assembly (dll) che implementa i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40a7e-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="40a7e-118">.NET Portability Analyzer (APIPort aka)</span><span class="sxs-lookup"><span data-stu-id="40a7e-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="40a7e-119">Ai moduli porta scritti per Windows PowerShell per lavorare con PowerShell Core, iniziare con il [.NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="40a7e-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="40a7e-120">Eseguire questo strumento per l'assembly compilato per determinare se le API .NET usato nel modulo sono compatibili con .NET Framework, .NET Core e altri Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="40a7e-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="40a7e-121">Lo strumento consiglia API alternative se presenti.</span><span class="sxs-lookup"><span data-stu-id="40a7e-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="40a7e-122">In caso contrario, potrebbe essere necessario aggiungere [controlli di runtime][] e limitare la funzionalità non disponibili nei runtime specifici.</span><span class="sxs-lookup"><span data-stu-id="40a7e-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="40a7e-123">Creare un nuovo modulo</span><span class="sxs-lookup"><span data-stu-id="40a7e-123">Creating a New Module</span></span>

<span data-ttu-id="40a7e-124">Se si crea un nuovo modulo, è consigliabile usare la [INTERFACCIA CLI DI .NET][].</span><span class="sxs-lookup"><span data-stu-id="40a7e-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="40a7e-125">Installazione del modello di modulo di PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="40a7e-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="40a7e-126">Dopo aver installata l'interfaccia CLI di .NET, installare una libreria di modelli per generare un semplice modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40a7e-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="40a7e-127">Il modulo potrà essere compatibile con Windows PowerShell, PowerShell Core, Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="40a7e-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="40a7e-128">Nell'esempio seguente viene illustrato come installare il modello:</span><span class="sxs-lookup"><span data-stu-id="40a7e-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="40a7e-129">Crea un nuovo progetto di modulo</span><span class="sxs-lookup"><span data-stu-id="40a7e-129">Creating a New Module Project</span></span>

<span data-ttu-id="40a7e-130">Dopo aver installato il modello, è possibile creare un nuovo progetto di modulo di PowerShell utilizzando tale modello.</span><span class="sxs-lookup"><span data-stu-id="40a7e-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="40a7e-131">In questo esempio, il modulo di esempio viene chiamato 'myModule'.</span><span class="sxs-lookup"><span data-stu-id="40a7e-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="40a7e-132">Creazione del modulo</span><span class="sxs-lookup"><span data-stu-id="40a7e-132">Building the Module</span></span>

<span data-ttu-id="40a7e-133">Usare i comandi della CLI di .NET standard per compilare il progetto.</span><span class="sxs-lookup"><span data-stu-id="40a7e-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="40a7e-134">Test del modulo</span><span class="sxs-lookup"><span data-stu-id="40a7e-134">Testing the Module</span></span>

<span data-ttu-id="40a7e-135">Dopo aver compilato il modulo, è possibile importarlo ed eseguire il cmdlet di esempio.</span><span class="sxs-lookup"><span data-stu-id="40a7e-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="40a7e-136">Le sezioni seguenti descrivono in dettaglio alcune delle tecnologie usate da questo modello.</span><span class="sxs-lookup"><span data-stu-id="40a7e-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="40a7e-137">Libreria .NET standard</span><span class="sxs-lookup"><span data-stu-id="40a7e-137">.NET Standard Library</span></span>

<span data-ttu-id="40a7e-138">[.NET standard][] è una specifica formale delle API .NET che sono disponibili in tutte le implementazioni .NET.</span><span class="sxs-lookup"><span data-stu-id="40a7e-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="40a7e-139">Gestito codice destinato a .NET Standard funziona con le versioni di .NET Framework e .NET Core che sono compatibili con tale versione di .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="40a7e-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="40a7e-140">Anche se può esistere un'API in .NET Standard, l'implementazione di API in .NET Core può generare un `PlatformNotSupportedException` in fase di esecuzione, pertanto, per verificare la compatibilità con Windows PowerShell e PowerShell Core, la procedura consigliata consiste nell'eseguire i test per il modulo all'interno di entrambi gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="40a7e-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="40a7e-141">Anche eseguire test in Linux e macOS, se il modulo deve essere multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="40a7e-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="40a7e-142">Scelta di .NET Standard consente di garantire che, come il modulo si evolve, le API incompatibili non ottenere introdotti accidentalmente nel modulo.</span><span class="sxs-lookup"><span data-stu-id="40a7e-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="40a7e-143">Problemi di incompatibilità vengono individuati in fase di compilazione invece di runtime.</span><span class="sxs-lookup"><span data-stu-id="40a7e-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="40a7e-144">Tuttavia, non è necessario alla destinazione .NET Standard per un modulo per lavorare con Windows PowerShell e PowerShell Core, purché si utilizzino API compatibili.</span><span class="sxs-lookup"><span data-stu-id="40a7e-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="40a7e-145">Il linguaggio intermedio (IL) è compatibile tra i due Runtime.</span><span class="sxs-lookup"><span data-stu-id="40a7e-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="40a7e-146">È possibile scegliere .NET Framework 4.6.1, che è compatibile con .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="40a7e-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="40a7e-147">Se non si usano le API di fuori di .NET Standard 2.0, quindi il modulo funziona con PowerShell Core 6 senza ricompilazione.</span><span class="sxs-lookup"><span data-stu-id="40a7e-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="40a7e-148">Libreria Standard di PowerShell</span><span class="sxs-lookup"><span data-stu-id="40a7e-148">PowerShell Standard Library</span></span>

<span data-ttu-id="40a7e-149">Il [Standard di PowerShell][] libreria è una specifica formale delle APIs PowerShell disponibili in tutte le versioni di PowerShell maggiore o uguale alla versione di tale standard.</span><span class="sxs-lookup"><span data-stu-id="40a7e-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="40a7e-150">Ad esempio, [Standard di PowerShell 5.1][] è compatibile con Windows PowerShell 5.1 e PowerShell Core 6.0 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="40a7e-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="40a7e-151">È consigliabile che si compila il modulo usando la libreria Standard di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40a7e-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="40a7e-152">La libreria garantisce che le API sono disponibili e implementate in Windows PowerShell e PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="40a7e-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="40a7e-153">Standard di PowerShell deve sempre essere compatibile con l'inoltro.</span><span class="sxs-lookup"><span data-stu-id="40a7e-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="40a7e-154">Un modulo compilato utilizzando PowerShell 5.1 libreria Standard saranno sempre compatibile con le versioni future di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40a7e-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="40a7e-155">Manifesto del modulo</span><span class="sxs-lookup"><span data-stu-id="40a7e-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="40a7e-156">Che indica la compatibilità con Windows PowerShell e PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="40a7e-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="40a7e-157">Dopo aver verificato che il modulo funziona con Windows PowerShell e PowerShell Core, il manifesto del modulo deve indicare in modo esplicito la compatibilità con le [CompatiblePSEditions][] proprietà.</span><span class="sxs-lookup"><span data-stu-id="40a7e-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="40a7e-158">Un valore pari `Desktop` significa che il modulo è compatibile con Windows PowerShell, mentre un valore di `Core` significa che il modulo è compatibile con PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="40a7e-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="40a7e-159">Inclusi i `Desktop` e `Core` significa che il modulo è compatibile con Windows PowerShell e PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="40a7e-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="40a7e-160">`Core` non significa che il modulo è compatibile con Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="40a7e-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="40a7e-161">Il **CompatiblePSEditions** proprietà è stato introdotto in PowerShell versione 5.</span><span class="sxs-lookup"><span data-stu-id="40a7e-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="40a7e-162">Modulo manifesti che utilizzano le **CompatiblePSEditions** caricamento nelle versioni precedenti a PowerShell versione 5 proprietà ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="40a7e-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="40a7e-163">Che indica la compatibilità del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="40a7e-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="40a7e-164">Per prima cosa, verificare che il modulo di funzioni in Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="40a7e-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="40a7e-165">Successivamente, indicano la compatibilità con il sistema operativo nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="40a7e-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="40a7e-166">Questo rende più semplice agli utenti di trovare un modulo per il proprio sistema operativo quando pubblicato per la [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="40a7e-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="40a7e-167">Nel manifesto del modulo, il `PrivateData` proprietà ha un `PSData` sottoproprietà.</span><span class="sxs-lookup"><span data-stu-id="40a7e-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="40a7e-168">L'opzione facoltativa `Tags` proprietà di `PSData` accetta una matrice di valori che vengono visualizzati in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="40a7e-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="40a7e-169">PowerShell Gallery supporta i seguenti valori di compatibilità:</span><span class="sxs-lookup"><span data-stu-id="40a7e-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="40a7e-170">Tag</span><span class="sxs-lookup"><span data-stu-id="40a7e-170">Tag</span></span>               | <span data-ttu-id="40a7e-171">Description</span><span class="sxs-lookup"><span data-stu-id="40a7e-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="40a7e-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="40a7e-172">PSEdition_Core</span></span>    | <span data-ttu-id="40a7e-173">Compatibile con PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="40a7e-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="40a7e-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="40a7e-174">PSEdition_Desktop</span></span> | <span data-ttu-id="40a7e-175">Compatibile con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="40a7e-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="40a7e-176">Windows</span><span class="sxs-lookup"><span data-stu-id="40a7e-176">Windows</span></span>           | <span data-ttu-id="40a7e-177">Compatibile con Windows</span><span class="sxs-lookup"><span data-stu-id="40a7e-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="40a7e-178">Linux</span><span class="sxs-lookup"><span data-stu-id="40a7e-178">Linux</span></span>             | <span data-ttu-id="40a7e-179">Compatibile con Linux (Nessuna distribuzione specifica)</span><span class="sxs-lookup"><span data-stu-id="40a7e-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="40a7e-180">macOS</span><span class="sxs-lookup"><span data-stu-id="40a7e-180">macOS</span></span>             | <span data-ttu-id="40a7e-181">Compatibile con macOS</span><span class="sxs-lookup"><span data-stu-id="40a7e-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="40a7e-182">Esempio:</span><span class="sxs-lookup"><span data-stu-id="40a7e-182">Example:</span></span>

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
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[INTERFACCIA CLI DI .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Standard di PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[Standard di PowerShell 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
