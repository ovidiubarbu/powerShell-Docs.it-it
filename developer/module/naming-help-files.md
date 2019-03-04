---
title: I file della Guida di denominazione | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856667"
---
# <a name="naming-help-files"></a><span data-ttu-id="53ae6-102">Denominazione dei file della Guida</span><span class="sxs-lookup"><span data-stu-id="53ae6-102">Naming Help Files</span></span>

<span data-ttu-id="53ae6-103">Questo argomento illustra come assegnare un nome di un file della Guida basati su XML in modo che il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet possibile trovarlo.</span><span class="sxs-lookup"><span data-stu-id="53ae6-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="53ae6-104">I requisiti di nomi variano per ogni tipo di comando.</span><span class="sxs-lookup"><span data-stu-id="53ae6-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="53ae6-105">Questo argomento illustra come assegnare un nome di un file della Guida basati su XML in modo che il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet possibile trovarlo.</span><span class="sxs-lookup"><span data-stu-id="53ae6-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="53ae6-106">I requisiti di nomi variano per ogni tipo di comando.</span><span class="sxs-lookup"><span data-stu-id="53ae6-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="53ae6-107">File della Guida dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="53ae6-107">Cmdlet Help Files</span></span>

<span data-ttu-id="53ae6-108">Il file della Guida per un C# cmdlet devono essere specificate per l'assembly in cui è definito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53ae6-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="53ae6-109">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="53ae6-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="53ae6-110">Il formato di nome di assembly è obbligatorio anche quando l'assembly è un modulo annidato.</span><span class="sxs-lookup"><span data-stu-id="53ae6-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="53ae6-111">Ad esempio, il [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet è definito nell'assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="53ae6-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="53ae6-112">Il `Get-Help` cmdlet Cerca un argomento della Guida per il `Get-WinEvent` cmdlet solo nel file Microsoft.PowerShell.Diagnostics.dll help.xml nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="53ae6-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="53ae6-113">Ad esempio, il [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet è definito nell'assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="53ae6-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="53ae6-114">Il `Get-Help` cmdlet Cerca un argomento della Guida per il `Get-WinEvent` cmdlet solo nel file Microsoft.PowerShell.Diagnostics.dll help.xml nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="53ae6-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="53ae6-115">File della Guida di provider</span><span class="sxs-lookup"><span data-stu-id="53ae6-115">Provider Help files</span></span>

<span data-ttu-id="53ae6-116">File della Guida per un provider di Windows PowerShell deve essere denominato per l'assembly in cui è definito il provider.</span><span class="sxs-lookup"><span data-stu-id="53ae6-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="53ae6-117">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="53ae6-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="53ae6-118">Il formato di nome di assembly è obbligatorio anche quando l'assembly è un modulo annidato.</span><span class="sxs-lookup"><span data-stu-id="53ae6-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="53ae6-119">Ad esempio, il provider Certificate è definito nell'assembly Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="53ae6-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="53ae6-120">Il `Get-Help` cmdlet Cerca un argomento della Guida per il provider Certificate solo nel file Microsoft.PowerShell.Security.dll help.xml nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="53ae6-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="53ae6-121">File della Guida (funzione)</span><span class="sxs-lookup"><span data-stu-id="53ae6-121">Function Help Files</span></span>

<span data-ttu-id="53ae6-122">Funzioni possono essere documentate con [della Guida basata sui commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentati nel file XML della Guida.</span><span class="sxs-lookup"><span data-stu-id="53ae6-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="53ae6-123">Quando la funzione è documentata in un file XML, la funzione deve avere un `.ExternalHelp` commento (parola chiave) che associa la funzione con il file XML.</span><span class="sxs-lookup"><span data-stu-id="53ae6-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="53ae6-124">In caso contrario, il `Get-Help` cmdlet non è possibile trovare il file della Guida.</span><span class="sxs-lookup"><span data-stu-id="53ae6-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="53ae6-125">Funzioni possono essere documentate con [della Guida basata sui commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentati nel file XML della Guida.</span><span class="sxs-lookup"><span data-stu-id="53ae6-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="53ae6-126">Quando la funzione è documentata in un file XML, la funzione deve avere un `.ExternalHelp` commento (parola chiave) che associa la funzione con il file XML.</span><span class="sxs-lookup"><span data-stu-id="53ae6-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="53ae6-127">In caso contrario, il `Get-Help` cmdlet non è possibile trovare il file della Guida.</span><span class="sxs-lookup"><span data-stu-id="53ae6-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="53ae6-128">Non sono previsti requisiti tecnici per il nome di un file della Guida funzione.</span><span class="sxs-lookup"><span data-stu-id="53ae6-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="53ae6-129">Tuttavia, una procedura consigliata è assegnare un nome file della Guida per il modulo di script in cui la funzione è definita.</span><span class="sxs-lookup"><span data-stu-id="53ae6-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="53ae6-130">Ad esempio, la funzione seguente è definita nel file MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="53ae6-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="53ae6-131">File della Guida comandi CIM</span><span class="sxs-lookup"><span data-stu-id="53ae6-131">CIM Command Help Files</span></span>

<span data-ttu-id="53ae6-132">Il file della Guida per un comando CIM deve essere denominato per il file CDXML in cui è definito il comando CIM.</span><span class="sxs-lookup"><span data-stu-id="53ae6-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="53ae6-133">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="53ae6-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="53ae6-134">I comandi CIM sono definiti nel file CDXML che possono essere inclusi nei moduli come i moduli annidati.</span><span class="sxs-lookup"><span data-stu-id="53ae6-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="53ae6-135">Quando il comando CIM viene importato nella sessione come una funzione, Windows PowerShell aggiunge un `.ExternalHelp` commento file di una parola chiave per la definizione di funzione che associa la funzione con un supporto XML è denominato per il file CDXML in cui è definito il comando CIM.</span><span class="sxs-lookup"><span data-stu-id="53ae6-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="53ae6-136">File della Guida del flusso di lavoro di script</span><span class="sxs-lookup"><span data-stu-id="53ae6-136">Script Workflow Help Files</span></span>

<span data-ttu-id="53ae6-137">I flussi di lavoro di script che sono inclusi nei moduli possono essere documentati nel file della Guida basati su XML.</span><span class="sxs-lookup"><span data-stu-id="53ae6-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="53ae6-138">Non sono previsti requisiti tecnici per il nome del file della Guida.</span><span class="sxs-lookup"><span data-stu-id="53ae6-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="53ae6-139">Tuttavia, una procedura consigliata è assegnare un nome file della Guida per il modulo di script in cui è definito il flusso di lavoro di script.</span><span class="sxs-lookup"><span data-stu-id="53ae6-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="53ae6-140">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="53ae6-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="53ae6-141">A differenza di altri comandi script, i flussi di lavoro di script non richiedono un `.ExternalHelp` commento parola chiave per associarle a un file della Guida.</span><span class="sxs-lookup"><span data-stu-id="53ae6-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="53ae6-142">Ma Windows PowerShell esegue la ricerca nelle sottodirectory specifiche di impostazioni cultura dell'interfaccia utente della directory del modulo per i file della Guida basati su XML e cerca la Guida per il flusso di lavoro di script in tutti i file.</span><span class="sxs-lookup"><span data-stu-id="53ae6-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="53ae6-143">`.ExternalHelp` parola chiave di commento vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="53ae6-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="53ae6-144">Poiché il `.ExternalHelp` parola chiave di commento viene ignorato, il `Get-Help` cmdlet potranno richiedere assistenza per i flussi di lavoro di script solo quando vengono inclusi nei moduli.</span><span class="sxs-lookup"><span data-stu-id="53ae6-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>