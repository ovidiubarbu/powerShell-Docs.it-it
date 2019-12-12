---
title: Come scrivere un modulo binario di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367120"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="9802a-102">Come scrivere un modulo binario di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9802a-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="9802a-103">Un modulo binario può essere qualsiasi assembly (. dll) che contiene le classi di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9802a-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="9802a-104">Per impostazione predefinita, tutti i cmdlet nell'assembly vengono importati quando viene importato il modulo binario.</span><span class="sxs-lookup"><span data-stu-id="9802a-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="9802a-105">Tuttavia, è possibile limitare i cmdlet importati creando un manifesto del modulo il cui modulo radice è l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9802a-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="9802a-106">(Ad esempio, la chiave CmdletsToExport del manifesto può essere usata per esportare solo i cmdlet necessari). Un modulo binario può inoltre contenere file aggiuntivi, una struttura di directory e altre informazioni di gestione utili che non possono essere utilizzate da un singolo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9802a-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="9802a-107">Nella procedura seguente viene descritto come creare e installare un modulo binario di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9802a-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="9802a-108">Come creare e installare un modulo binario di PowerShell</span><span class="sxs-lookup"><span data-stu-id="9802a-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="9802a-109">Creare una soluzione PowerShell binaria, ad esempio un cmdlet scritto C#in, con le funzionalità necessarie e assicurarsi che venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="9802a-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="9802a-110">Dal punto di vista del codice, il nucleo di un modulo binario è semplicemente un assembly di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9802a-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="9802a-111">In realtà, PowerShell tratterà un singolo assembly di cmdlet come modulo, in termini di caricamento e scaricamento, senza sforzi aggiuntivi da parte dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="9802a-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="9802a-112">Per ulteriori informazioni sulla scrittura di un cmdlet, vedere [scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="9802a-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="9802a-113">Se necessario, creare il resto della soluzione, ovvero i cmdlet aggiuntivi, i file XML e così via, e descriverli con un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="9802a-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="9802a-114">Oltre a descrivere gli assembly dei cmdlet nella soluzione, un manifesto del modulo può descrivere come si vuole che il modulo venga esportato e importato, quali cmdlet verranno esposti e quali file aggiuntivi verranno inseriti nel modulo.</span><span class="sxs-lookup"><span data-stu-id="9802a-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="9802a-115">Come indicato in precedenza, tuttavia, PowerShell può considerare un cmdlet binario come un modulo senza ulteriori sforzi.</span><span class="sxs-lookup"><span data-stu-id="9802a-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="9802a-116">Di conseguenza, un manifesto del modulo è particolarmente utile per combinare più file in un singolo pacchetto o per controllare in modo esplicito la pubblicazione per un determinato assembly.</span><span class="sxs-lookup"><span data-stu-id="9802a-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="9802a-117">Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="9802a-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="9802a-118">Il codice seguente è un blocco di C# codice estremamente semplice che contiene tre cmdlet nello stesso file che possono essere usati come modulo.</span><span class="sxs-lookup"><span data-stu-id="9802a-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="9802a-119">Creare il pacchetto della soluzione e salvare il pacchetto in un punto qualsiasi nel percorso del modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9802a-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="9802a-120">La variabile di ambiente globale `PSModulePath` descrive i percorsi predefiniti che verranno usati da PowerShell per individuare il modulo.</span><span class="sxs-lookup"><span data-stu-id="9802a-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="9802a-121">Un percorso comune per il salvataggio di un modulo in un sistema, ad esempio, sarebbe `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="9802a-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="9802a-122">Se non si usano i percorsi predefiniti, sarà necessario indicare in modo esplicito il percorso del modulo durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="9802a-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="9802a-123">Assicurarsi di creare una cartella in cui salvare il modulo, perché potrebbe essere necessaria la cartella per archiviare più assembly e file per la soluzione.</span><span class="sxs-lookup"><span data-stu-id="9802a-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="9802a-124">Si noti che tecnicamente non è necessario installare il modulo in un punto qualsiasi dell'`PSModulePath`, che sono semplicemente i percorsi predefiniti che verrà ricercato da PowerShell per il modulo.</span><span class="sxs-lookup"><span data-stu-id="9802a-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="9802a-125">Tuttavia, si tratta di una procedura consigliata, a meno che non si disponga di un buon motivo per archiviare il modulo altrove.</span><span class="sxs-lookup"><span data-stu-id="9802a-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="9802a-126">Per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md) e [modifica del percorso di installazione del modulo di PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="9802a-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="9802a-127">Importare il modulo in PowerShell con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="9802a-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="9802a-128">La chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) caricherà il modulo nella memoria attiva.</span><span class="sxs-lookup"><span data-stu-id="9802a-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="9802a-129">Se si usa PowerShell 3,0 e versioni successive, verrà importato anche il nome del modulo nel codice. per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="9802a-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="9802a-130">Importazione di assembly snap-in come moduli</span><span class="sxs-lookup"><span data-stu-id="9802a-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="9802a-131">I cmdlet e i provider presenti negli assembly snap-in possono essere caricati come moduli binari.</span><span class="sxs-lookup"><span data-stu-id="9802a-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="9802a-132">Quando gli assembly dello snap-in vengono caricati come moduli binari, i cmdlet e i provider nello snap-in sono disponibili per l'utente, ma la classe di snap-in nell'assembly viene ignorata e lo snap-in non è registrato.</span><span class="sxs-lookup"><span data-stu-id="9802a-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="9802a-133">Di conseguenza, i cmdlet dello snap-in forniti da Windows PowerShell non sono in grado di rilevare lo snap-in anche se i cmdlet e i provider sono disponibili per la sessione.</span><span class="sxs-lookup"><span data-stu-id="9802a-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="9802a-134">Inoltre, tutti i file di formattazione o di tipi a cui fa riferimento lo snap-in non possono essere importati come parte di un modulo binario.</span><span class="sxs-lookup"><span data-stu-id="9802a-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="9802a-135">Per importare i file di formattazione e dei tipi, è necessario creare un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="9802a-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="9802a-136">Vedere [come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="9802a-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9802a-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9802a-137">See Also</span></span>

[<span data-ttu-id="9802a-138">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9802a-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
