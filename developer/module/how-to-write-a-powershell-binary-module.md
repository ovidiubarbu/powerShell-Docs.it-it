---
title: Come scrivere un modulo di file binari di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229327"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="e3169-102">Come scrivere un modulo binario di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3169-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="e3169-103">Un modulo binario può essere qualsiasi assembly (DLL) che contiene le classi di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3169-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="e3169-104">Per impostazione predefinita, vengono importati tutti i cmdlet nell'assembly quando viene importato il modulo binario.</span><span class="sxs-lookup"><span data-stu-id="e3169-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="e3169-105">Tuttavia, è possibile limitare i cmdlet che vengono importati mediante la creazione di un manifesto del modulo il cui modulo radice è l'assembly.</span><span class="sxs-lookup"><span data-stu-id="e3169-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="e3169-106">(Ad esempio, la chiave CmdletsToExport del manifesto è utilizzabile per esportare solo i cmdlet necessari.) Inoltre, un modulo binario può contenere altre parti di tali informazioni utili che non è un singolo cmdlet, una struttura di directory e file aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="e3169-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="e3169-107">La procedura seguente viene descritto come creare e installare un modulo binario di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3169-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="e3169-108">Come creare e installare un modulo binario di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3169-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="e3169-109">Creare una soluzione binaria di PowerShell (ad esempio un cmdlet scritto in C#), con le funzionalità necessarie e garantire che venga eseguito correttamente.</span><span class="sxs-lookup"><span data-stu-id="e3169-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="e3169-110">Dalla prospettiva del codice, il nucleo di un modulo binario è semplicemente un assembly di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3169-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="e3169-111">In effetti, PowerShell considererà assembly un singolo cmdlet come un modulo, in termini di caricamento e scaricamento, senza ulteriori interventi da parte dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="e3169-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="e3169-112">Per altre informazioni sulla scrittura di un cmdlet, vedere [scrittura di un Cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="e3169-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="e3169-113">Se necessario, creare il resto della soluzione: (altri cmdlet, i file XML e così via) e vengono descritte con un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="e3169-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="e3169-114">Oltre a descrivere gli assembly di cmdlet nella soluzione, è possibile descrivere un manifesto del modulo come si desidera che il modulo esportati e importati, i cmdlet che verranno esposto e quali file aggiuntivi diventeranno il modulo.</span><span class="sxs-lookup"><span data-stu-id="e3169-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="e3169-115">Come indicato in precedenza, tuttavia, un cmdlet binario, ad esempio un modulo con un impegno aggiuntivo può gestire con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3169-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="e3169-116">Di conseguenza, un manifesto del modulo è utile principalmente per la combinazione di più file in un singolo pacchetto o per il controllo in modo esplicito di pubblicazione per un determinato assembly.</span><span class="sxs-lookup"><span data-stu-id="e3169-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="e3169-117">Per altre informazioni, vedere [come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="e3169-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="e3169-118">Il codice seguente è un'operazione estremamente semplice C# blocco di codice che contiene tre cmdlet nello stesso file che può essere utilizzato come un modulo.</span><span class="sxs-lookup"><span data-stu-id="e3169-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="e3169-119">Creare un pacchetto della soluzione e salvare il pacchetto a una destinazione nel percorso del modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3169-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="e3169-120">Il `PSModulePath` variabile di ambiente globali vengono descritti i percorsi predefiniti che PowerShell utilizzerà per individuare un modulo.</span><span class="sxs-lookup"><span data-stu-id="e3169-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="e3169-121">Ad esempio, potrebbe essere un percorso comune per salvare un modulo in un sistema `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="e3169-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="e3169-122">Se non si utilizza il percorso predefinito, è necessario dichiarare in modo esplicito il percorso del modulo durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="e3169-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="e3169-123">Assicurarsi di creare una cartella in cui salvare il modulo, si potrebbe avere bisogno la cartella per archiviare più assembly e file per la soluzione.</span><span class="sxs-lookup"><span data-stu-id="e3169-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="e3169-124">Si noti che tecnicamente non occorre installare un modulo in qualsiasi punto nel `PSModulePath` -sono semplicemente i percorsi predefiniti che eseguirà la ricerca per il modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3169-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="e3169-125">Tuttavia, viene considerato ottimale per eseguire questa operazione, a meno che non si dispone di un buon motivo per l'archiviazione di un modulo in un'altra posizione.</span><span class="sxs-lookup"><span data-stu-id="e3169-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="e3169-126">Per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md) e [modifica il percorso di installazione del modulo PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="e3169-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="e3169-127">Importare un modulo in PowerShell con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="e3169-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="e3169-128">La chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) caricherà un modulo in memoria attiva.</span><span class="sxs-lookup"><span data-stu-id="e3169-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="e3169-129">Se si usa PowerShell 3.0 e versioni successive, chiamare semplicemente il nome del modulo nel codice verrà anche importare i dati; per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="e3169-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="e3169-130">Importazione Snap-in assembly come moduli</span><span class="sxs-lookup"><span data-stu-id="e3169-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="e3169-131">Cmdlet e provider presenti negli assembly snap-in può essere caricato come moduli binari.</span><span class="sxs-lookup"><span data-stu-id="e3169-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="e3169-132">Quando l'assembly snap-in vengono caricati come moduli binari, i cmdlet e provider nello snap-in sono disponibili all'utente, ma la classe di snap-nell'assembly viene ignorata e lo snap-in non è registrato.</span><span class="sxs-lookup"><span data-stu-id="e3169-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="e3169-133">Di conseguenza, i cmdlet di snap-in di Windows PowerShell non è possibile rilevare lo snap-in anche con i cmdlet e provider disponibili nella sessione.</span><span class="sxs-lookup"><span data-stu-id="e3169-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="e3169-134">Inoltre, qualsiasi formattazione o tipi di file che fanno riferimento lo snap-in non è possibile importare come parte di un modulo binario.</span><span class="sxs-lookup"><span data-stu-id="e3169-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="e3169-135">Per importare i file di formattazione e tipi è necessario creare un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="e3169-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="e3169-136">Vedere [come scrivere un manifesto del modulo di PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="e3169-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3169-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e3169-137">See Also</span></span>

[<span data-ttu-id="e3169-138">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3169-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
