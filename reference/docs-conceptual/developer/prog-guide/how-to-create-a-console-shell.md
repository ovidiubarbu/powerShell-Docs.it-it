---
title: Come creare una shell della console | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360270"
---
# <a name="how-to-create-a-console-shell"></a><span data-ttu-id="d621f-102">Come creare una shell di console</span><span class="sxs-lookup"><span data-stu-id="d621f-102">How to Create a Console Shell</span></span>

<span data-ttu-id="d621f-103">Windows PowerShell offre uno strumento di creazione della shell, noto anche come "make-Kit", che viene usato per creare una shell della console non estendibile.</span><span class="sxs-lookup"><span data-stu-id="d621f-103">Windows PowerShell provides a Make-Shell tool, also referred to as the "make-kit", that is used to create a console shell that is not extensible.</span></span> <span data-ttu-id="d621f-104">Le shell create con questo nuovo strumento non possono essere estese in un secondo momento tramite uno snap-in di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d621f-104">Shells created with this new tool cannot be extended later through a Windows PowerShell snap-in.</span></span>

## <a name="syntax"></a><span data-ttu-id="d621f-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d621f-105">Syntax</span></span>

<span data-ttu-id="d621f-106">Di seguito è illustrata la sintassi usata per eseguire make-Shell dall'interno di un file.</span><span class="sxs-lookup"><span data-stu-id="d621f-106">Here is the syntax used to run Make-Shell from within a make-file.</span></span>

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a><span data-ttu-id="d621f-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="d621f-107">Parameters</span></span>

<span data-ttu-id="d621f-108">Ecco una breve descrizione dei parametri di make-Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-108">Here is a brief description of the parameters of Make-Shell.</span></span>

> [!CAUTION]
> <span data-ttu-id="d621f-109">I percorsi UNC degli assembly non sono supportati da make-Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-109">UNC paths to assemblies are not supported by Make-Shell.</span></span>

|<span data-ttu-id="d621f-110">Parametro</span><span class="sxs-lookup"><span data-stu-id="d621f-110">Parameter</span></span>|<span data-ttu-id="d621f-111">Description</span><span class="sxs-lookup"><span data-stu-id="d621f-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d621f-112">-out n. exe</span><span class="sxs-lookup"><span data-stu-id="d621f-112">-out n.exe</span></span>|<span data-ttu-id="d621f-113">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d621f-113">Required.</span></span> <span data-ttu-id="d621f-114">Nome della shell da produrre.</span><span class="sxs-lookup"><span data-stu-id="d621f-114">The name of the shell to produce.</span></span> <span data-ttu-id="d621f-115">Il percorso viene specificato come parte di questo parametro.</span><span class="sxs-lookup"><span data-stu-id="d621f-115">The path is specified as part of this parameter.</span></span><br /><br /> <span data-ttu-id="d621f-116">Se non è specificato, la funzione Make-shell aggiungerà ". exe" a questo valore.</span><span class="sxs-lookup"><span data-stu-id="d621f-116">Make-shell will append ".exe" to this value if it is not specified.</span></span> <span data-ttu-id="d621f-117">**Attenzione:**  Non creare un file di output con lo stesso nome del file con estensione dll a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="d621f-117">**Caution:**  Do not create an output file with the same name as the referenced .dll file.</span></span> <span data-ttu-id="d621f-118">Se si tenta di eseguire questa operazione, lo strumento make-shell crea un file con estensione cs con lo stesso nome, che sovrascriverà il file con estensione cs con il codice sorgente del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d621f-118">If you attempt this, the Make-Shell tool creates a .cs file with the same name, which will overwrite the .cs file that has your cmdlet source code.</span></span>|
|<span data-ttu-id="d621f-119">-spazio dei nomi NS</span><span class="sxs-lookup"><span data-stu-id="d621f-119">-namespace ns</span></span>|<span data-ttu-id="d621f-120">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d621f-120">Required.</span></span> <span data-ttu-id="d621f-121">Lo spazio dei nomi da usare per la classe [System. Management. Automation. Runspaces. RunspaceConfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) derivata che il kit genera e compila.</span><span class="sxs-lookup"><span data-stu-id="d621f-121">The namespace to use for the derived [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) class that the make-kit generates and compiles.</span></span>|
|<span data-ttu-id="d621f-122">-lib libdirectory1 [, libdirectory2,..]</span><span class="sxs-lookup"><span data-stu-id="d621f-122">-lib libdirectory1[,libdirectory2,..]</span></span>|<span data-ttu-id="d621f-123">Directory in cui vengono cercati gli assembly .NET, inclusi gli assembly di Windows PowerShell, gli assembly specificati dal parametro `reference`, gli assembly a cui fa riferimento indirettamente un altro assembly e gli assembly di sistema .NET.</span><span class="sxs-lookup"><span data-stu-id="d621f-123">The directories that are searched for .NET assemblies, including the Windows PowerShell assemblies, assemblies specified by the `reference` parameter, assemblies indirectly referenced by another assembly, and the .NET system assemblies.</span></span>|
|<span data-ttu-id="d621f-124">-Reference CA1. dll [, Ca2. dll,...]</span><span class="sxs-lookup"><span data-stu-id="d621f-124">-reference ca1.dll[,ca2.dll,...]</span></span>|<span data-ttu-id="d621f-125">Elenco delimitato da virgole degli assembly da includere nella shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-125">A comma-separated list of the assemblies to include in the shell.</span></span> <span data-ttu-id="d621f-126">Questi assembly includono tutti gli assembly di cmdlet e provider, nonché gli assembly di risorse che devono essere caricati.</span><span class="sxs-lookup"><span data-stu-id="d621f-126">These assemblies  includes all cmdlet and provider assemblies, as well as resource assemblies that should be loaded.</span></span> <span data-ttu-id="d621f-127">Se questo parametro non è specificato, viene generata una shell che contiene solo i cmdlet e i provider principali forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d621f-127">If this parameter is not specified, then a shell is produced that contains only the core cmdlets and providers provided by Windows PowerShell.</span></span><br /><br /> <span data-ttu-id="d621f-128">Gli assembly possono essere specificati utilizzando il percorso completo; in caso contrario, verranno cercati utilizzando il percorso specificato dal parametro `lib`.</span><span class="sxs-lookup"><span data-stu-id="d621f-128">The assemblies can be specified using their full path, otherwise they will be searched for using the path specified by the `lib` parameter.</span></span>|
|<span data-ttu-id="d621f-129">-FormatData FD1. Format. ps1xml [, FD2. Format. ps1xml,...]</span><span class="sxs-lookup"><span data-stu-id="d621f-129">-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]</span></span>|<span data-ttu-id="d621f-130">Elenco delimitato da virgole dei dati di formato da includere nella shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-130">A comma-separated list of format data to include in the shell.</span></span> <span data-ttu-id="d621f-131">Se questo parametro non è specificato, viene generata una shell che contiene solo i dati di formato forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d621f-131">If this parameter is not specified, then a shell is produced that contains only the format data provided by Windows PowerShell.</span></span>|
|<span data-ttu-id="d621f-132">-TypeData TD1. Type. ps1xml [, TD2. Type. ps1xml,...]</span><span class="sxs-lookup"><span data-stu-id="d621f-132">-typedata td1.type.ps1xml[,td2.type.ps1xml,...]</span></span>|<span data-ttu-id="d621f-133">Elenco delimitato da virgole di dati di tipo da includere nella shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-133">A comma-separated list of type data to include in the shell.</span></span> <span data-ttu-id="d621f-134">Se questo parametro non è specificato, viene generata una shell che contiene solo i dati di tipo forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d621f-134">If this parameter is not specified, then a shell is produced that contains only the type data provided by Windows PowerShell.</span></span>|
|<span data-ttu-id="d621f-135">-Source c1.cs [, c2.cs,...]</span><span class="sxs-lookup"><span data-stu-id="d621f-135">-source c1.cs [,c2.cs,...]</span></span>|<span data-ttu-id="d621f-136">Nome di un file, fornito dallo sviluppatore della shell, che contiene il codice sorgente necessario per compilare la Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-136">The name of a file, provided by the shell developer, that contains any source code needed to build the shell.</span></span><br /><br /> <span data-ttu-id="d621f-137">Il file di codice sorgente può contenere uno qualsiasi dei seguenti codici sorgente:</span><span class="sxs-lookup"><span data-stu-id="d621f-137">The source code file can contain any of the following source code:</span></span><br /><br /> <span data-ttu-id="d621f-138">: Implementazione di gestione autorizzazioni che esegue l'override del gestore autorizzazioni predefinito.</span><span class="sxs-lookup"><span data-stu-id="d621f-138">-   The Authorization manager implementation that overrides the default authorization manager.</span></span> <span data-ttu-id="d621f-139">Questa operazione può anche essere compilata in un assembly.</span><span class="sxs-lookup"><span data-stu-id="d621f-139">(This could also be supplied compiled into an assembly.)</span></span><br /><span data-ttu-id="d621f-140">-Dichiarazioni dell'attributo informativo sugli assembly: ad esempio AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute e AssemblyTrademarkAttribute.</span><span class="sxs-lookup"><span data-stu-id="d621f-140">-   Assembly informational attribute declarations: such as the AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, and AssemblyTrademarkAttribute.</span></span>|
|<span data-ttu-id="d621f-141">-AuthorizationManager authorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="d621f-141">-authorizationmanager authorizationManagerType</span></span>|<span data-ttu-id="d621f-142">Tipo che contiene l'implementazione di gestione autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="d621f-142">The type that contains the authorization manager implementation.</span></span> <span data-ttu-id="d621f-143">Questo può essere definito nel codice sorgente o compilato in un assembly (specificato dal parametro `reference`).</span><span class="sxs-lookup"><span data-stu-id="d621f-143">This can be defined in source code, or compiled into an assembly (specified by the `reference` parameter).</span></span> <span data-ttu-id="d621f-144">Se questo parametro non viene specificato, viene utilizzato il gestore sicurezza predefinito.</span><span class="sxs-lookup"><span data-stu-id="d621f-144">If this parameter is not specified, the default security manager is used.</span></span> <span data-ttu-id="d621f-145">Il valore deve essere il nome completo del tipo, inclusi gli spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="d621f-145">The value should be the full type name, including namespaces.</span></span>|
|<span data-ttu-id="d621f-146">-win32icon i. ico</span><span class="sxs-lookup"><span data-stu-id="d621f-146">-win32icon i.ico</span></span>|<span data-ttu-id="d621f-147">Icona del file exe per la Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-147">The icon for the .exe file for the shell.</span></span> <span data-ttu-id="d621f-148">Se non è specificato, la shell avrà l'icona che il compilatore c# include (se presente).</span><span class="sxs-lookup"><span data-stu-id="d621f-148">If not specified, then the shell will have the icon that the c# compiler includes (if any).</span></span>|
|<span data-ttu-id="d621f-149">-initscript p. ps1</span><span class="sxs-lookup"><span data-stu-id="d621f-149">-initscript p.ps1</span></span>|<span data-ttu-id="d621f-150">Profilo di avvio per la Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-150">The startup profile for the shell.</span></span> <span data-ttu-id="d621f-151">Il file è incluso "così com'è"; non viene eseguita alcuna verifica della validità da make-Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-151">The file is included "as-is"; no validity checking is done by Make-Shell.</span></span>|
|<span data-ttu-id="d621f-152">-builtinscript S1. ps1 [, S2. ps1,...]</span><span class="sxs-lookup"><span data-stu-id="d621f-152">-builtinscript s1.ps1[,s2.ps1,...]</span></span>|<span data-ttu-id="d621f-153">Elenco di script predefiniti per la Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-153">A list of built-in scripts for the shell.</span></span> <span data-ttu-id="d621f-154">Questi script vengono individuati prima degli script nel percorso e il relativo contenuto non può essere modificato dopo la compilazione della shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-154">These scripts are discovered before scripts in the path, and their contents cannot be changed once the shell is built.</span></span><br /><br /> <span data-ttu-id="d621f-155">I file sono inclusi "così come sono"; non viene eseguita alcuna verifica della validità da make-Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-155">The files are included "as-is"; no validity checking is done by Make-Shell.</span></span>|
|<span data-ttu-id="d621f-156">-Resource resourceFile. txt</span><span class="sxs-lookup"><span data-stu-id="d621f-156">-resource resourcefile.txt</span></span>|<span data-ttu-id="d621f-157">Il file con estensione txt contenente le risorse della guida e del banner per la Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-157">The .txt file containing help and banner resources for the shell.</span></span> <span data-ttu-id="d621f-158">La prima risorsa è denominata ShellHelp e contiene il testo visualizzato se la shell viene richiamata con il parametro `help`.</span><span class="sxs-lookup"><span data-stu-id="d621f-158">The first resource is named ShellHelp, and contains the text displayed if the shell is invoked with the `help` parameter.</span></span> <span data-ttu-id="d621f-159">La seconda risorsa è denominata ShellBanner e contiene il testo e le informazioni sul copyright visualizzate quando la shell viene avviata in modalità interattiva.</span><span class="sxs-lookup"><span data-stu-id="d621f-159">The second resource is named ShellBanner, and it contains the text and copyright information displayed when the shell is launched in interactive mode.</span></span><br /><br /> <span data-ttu-id="d621f-160">Se questo parametro non viene fornito o se queste risorse non sono presenti, vengono usate una guida generica e un banner.</span><span class="sxs-lookup"><span data-stu-id="d621f-160">If this parameter is not provided, or these resources are not present, then a generic help and banner are used.</span></span>|
|<span data-ttu-id="d621f-161">-cscflags cscFlags</span><span class="sxs-lookup"><span data-stu-id="d621f-161">-cscflags cscFlags</span></span>|<span data-ttu-id="d621f-162">Flag che devono essere passati al C# compilatore (CSC. exe).</span><span class="sxs-lookup"><span data-stu-id="d621f-162">Flags that should be passed to the C# compiler (csc.exe).</span></span> <span data-ttu-id="d621f-163">Questi vengono passati senza modifiche.</span><span class="sxs-lookup"><span data-stu-id="d621f-163">These are passed through unchanged.</span></span> <span data-ttu-id="d621f-164">Se questo parametro include spazi, deve essere racchiuso tra virgolette doppie.</span><span class="sxs-lookup"><span data-stu-id="d621f-164">If this parameter includes spaces, it should be surrounded in double-quotes.</span></span>|
|<span data-ttu-id="d621f-165">-?</span><span class="sxs-lookup"><span data-stu-id="d621f-165">-?</span></span><br /><br /> <span data-ttu-id="d621f-166">-Guida in linea</span><span class="sxs-lookup"><span data-stu-id="d621f-166">-help</span></span>|<span data-ttu-id="d621f-167">Visualizza il messaggio di copyright e le opzioni della riga di comando di make-Shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-167">Displays the copyright message and Make-Shell command line options.</span></span>|
|<span data-ttu-id="d621f-168">-Verbose</span><span class="sxs-lookup"><span data-stu-id="d621f-168">-verbose</span></span>|<span data-ttu-id="d621f-169">Visualizza informazioni dettagliate durante la creazione della shell.</span><span class="sxs-lookup"><span data-stu-id="d621f-169">Displays detailed information while the shell is being created.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d621f-170">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d621f-170">See Also</span></span>

[<span data-ttu-id="d621f-171">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d621f-171">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d621f-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d621f-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)