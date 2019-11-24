---
title: Denominazione dei file della Guida | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367010"
---
# <a name="naming-help-files"></a><span data-ttu-id="36b78-102">Denominazione dei file della Guida</span><span class="sxs-lookup"><span data-stu-id="36b78-102">Naming Help Files</span></span>

<span data-ttu-id="36b78-103">In questo argomento viene illustrato come assegnare un nome a un file della guida basato su XML in modo che il cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) possa trovarlo.</span><span class="sxs-lookup"><span data-stu-id="36b78-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="36b78-104">I requisiti del nome variano a seconda del tipo di comando.</span><span class="sxs-lookup"><span data-stu-id="36b78-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="36b78-105">File della Guida dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="36b78-105">Cmdlet Help Files</span></span>

<span data-ttu-id="36b78-106">Il nome del file della C# guida per un cmdlet deve essere relativo all'assembly in cui è definito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36b78-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="36b78-107">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="36b78-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="36b78-108">Il formato del nome dell'assembly è obbligatorio anche quando l'assembly è un modulo annidato.</span><span class="sxs-lookup"><span data-stu-id="36b78-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="36b78-109">Ad esempio, [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) il cmdlet è definito nell'assembly Microsoft. PowerShell. Diagnostics. dll.</span><span class="sxs-lookup"><span data-stu-id="36b78-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="36b78-110">Il cmdlet `Get-Help` Cerca un argomento della Guida per il cmdlet `Get-WinEvent` solo nel file Microsoft. PowerShell. Diagnostics. dll-help. XML nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="36b78-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="36b78-111">File della guida del provider</span><span class="sxs-lookup"><span data-stu-id="36b78-111">Provider Help files</span></span>

<span data-ttu-id="36b78-112">Il file della Guida per un provider di Windows PowerShell deve essere denominato per l'assembly in cui è definito il provider.</span><span class="sxs-lookup"><span data-stu-id="36b78-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="36b78-113">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="36b78-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="36b78-114">Il formato del nome dell'assembly è obbligatorio anche quando l'assembly è un modulo annidato.</span><span class="sxs-lookup"><span data-stu-id="36b78-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="36b78-115">Ad esempio, il provider di certificati viene definito nell'assembly Microsoft. PowerShell. Security. dll.</span><span class="sxs-lookup"><span data-stu-id="36b78-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="36b78-116">Il cmdlet `Get-Help` Cerca un argomento della Guida per il provider di certificati solo nel file Microsoft. PowerShell. Security. dll-help. XML nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="36b78-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="36b78-117">File della Guida per le funzioni</span><span class="sxs-lookup"><span data-stu-id="36b78-117">Function Help Files</span></span>

<span data-ttu-id="36b78-118">Per documentare le funzioni, è possibile usare la [Guida basata su Commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentata in un file della Guida XML.</span><span class="sxs-lookup"><span data-stu-id="36b78-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="36b78-119">Quando la funzione è documentata in un file XML, la funzione deve avere una parola chiave `.ExternalHelp` commento che associa la funzione al file XML.</span><span class="sxs-lookup"><span data-stu-id="36b78-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="36b78-120">In caso contrario, il cmdlet `Get-Help` non riesce a trovare il file della guida.</span><span class="sxs-lookup"><span data-stu-id="36b78-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="36b78-121">Non sono previsti requisiti tecnici per il nome di un file della Guida per le funzioni.</span><span class="sxs-lookup"><span data-stu-id="36b78-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="36b78-122">Tuttavia, una procedura consigliata consiste nel denominare il file della Guida per il modulo di script in cui la funzione è definita.</span><span class="sxs-lookup"><span data-stu-id="36b78-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="36b78-123">Ad esempio, la funzione seguente viene definita nel file con estensione psm1.</span><span class="sxs-lookup"><span data-stu-id="36b78-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="36b78-124">File della guida del comando CIM</span><span class="sxs-lookup"><span data-stu-id="36b78-124">CIM Command Help Files</span></span>

<span data-ttu-id="36b78-125">Il file della Guida per un comando CIM deve essere denominato per il file CDXML in cui è definito il comando CIM.</span><span class="sxs-lookup"><span data-stu-id="36b78-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="36b78-126">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="36b78-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="36b78-127">I comandi CIM sono definiti nei file CDXML che possono essere inclusi nei moduli come moduli annidati.</span><span class="sxs-lookup"><span data-stu-id="36b78-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="36b78-128">Quando il comando CIM viene importato nella sessione come funzione, Windows PowerShell aggiunge una parola chiave `.ExternalHelp` comment alla definizione di funzione che associa la funzione a un file della Guida XML denominato per il file CDXML in cui è definito il comando CIM.</span><span class="sxs-lookup"><span data-stu-id="36b78-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="36b78-129">File della guida del flusso di lavoro script</span><span class="sxs-lookup"><span data-stu-id="36b78-129">Script Workflow Help Files</span></span>

<span data-ttu-id="36b78-130">I flussi di lavoro di script inclusi nei moduli possono essere documentati in file della Guida basati su XML.</span><span class="sxs-lookup"><span data-stu-id="36b78-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="36b78-131">Non sono previsti requisiti tecnici per il nome del file della guida.</span><span class="sxs-lookup"><span data-stu-id="36b78-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="36b78-132">Tuttavia, una procedura consigliata consiste nel denominare il file della Guida per il modulo di script in cui viene definito il flusso di lavoro di script.</span><span class="sxs-lookup"><span data-stu-id="36b78-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="36b78-133">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="36b78-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="36b78-134">A differenza di altri comandi con script, i flussi di lavoro di script non richiedono una parola chiave di commento `.ExternalHelp` per associarli a un file della guida.</span><span class="sxs-lookup"><span data-stu-id="36b78-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="36b78-135">Windows PowerShell cerca invece le sottodirectory specifiche delle impostazioni cultura dell'interfaccia utente della directory dei moduli per i file della Guida basati su XML e cerca la guida per il flusso di lavoro di script in tutti i file.</span><span class="sxs-lookup"><span data-stu-id="36b78-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="36b78-136">`.ExternalHelp` parola chiave comment viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="36b78-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="36b78-137">Poiché la parola chiave `.ExternalHelp` comment viene ignorata, il cmdlet `Get-Help` può trovare la guida per i flussi di lavoro di script solo quando sono inclusi nei moduli.</span><span class="sxs-lookup"><span data-stu-id="36b78-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>