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
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082179"
---
# <a name="naming-help-files"></a><span data-ttu-id="15f22-102">Denominazione dei file della Guida</span><span class="sxs-lookup"><span data-stu-id="15f22-102">Naming Help Files</span></span>

<span data-ttu-id="15f22-103">Questo argomento illustra come assegnare un nome di un file della Guida basati su XML in modo che il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet possibile trovarlo.</span><span class="sxs-lookup"><span data-stu-id="15f22-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="15f22-104">I requisiti di nomi variano per ogni tipo di comando.</span><span class="sxs-lookup"><span data-stu-id="15f22-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="15f22-105">File della Guida dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f22-105">Cmdlet Help Files</span></span>

<span data-ttu-id="15f22-106">Il file della Guida per un C# cmdlet devono essere specificate per l'assembly in cui è definito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f22-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="15f22-107">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="15f22-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="15f22-108">Il formato di nome di assembly è obbligatorio anche quando l'assembly è un modulo annidato.</span><span class="sxs-lookup"><span data-stu-id="15f22-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="15f22-109">Ad esempio, il [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet è definito nell'assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="15f22-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="15f22-110">Il `Get-Help` cmdlet Cerca un argomento della Guida per il `Get-WinEvent` cmdlet solo nel file Microsoft.PowerShell.Diagnostics.dll help.xml nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="15f22-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="15f22-111">File della Guida di provider</span><span class="sxs-lookup"><span data-stu-id="15f22-111">Provider Help files</span></span>

<span data-ttu-id="15f22-112">File della Guida per un provider di Windows PowerShell deve essere denominato per l'assembly in cui è definito il provider.</span><span class="sxs-lookup"><span data-stu-id="15f22-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="15f22-113">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="15f22-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="15f22-114">Il formato di nome di assembly è obbligatorio anche quando l'assembly è un modulo annidato.</span><span class="sxs-lookup"><span data-stu-id="15f22-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="15f22-115">Ad esempio, il provider Certificate è definito nell'assembly Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="15f22-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="15f22-116">Il `Get-Help` cmdlet Cerca un argomento della Guida per il provider Certificate solo nel file Microsoft.PowerShell.Security.dll help.xml nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="15f22-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="15f22-117">File della Guida (funzione)</span><span class="sxs-lookup"><span data-stu-id="15f22-117">Function Help Files</span></span>

<span data-ttu-id="15f22-118">Funzioni possono essere documentate con [della Guida basata sui commenti](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentati nel file XML della Guida.</span><span class="sxs-lookup"><span data-stu-id="15f22-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="15f22-119">Quando la funzione è documentata in un file XML, la funzione deve avere un `.ExternalHelp` commento (parola chiave) che associa la funzione con il file XML.</span><span class="sxs-lookup"><span data-stu-id="15f22-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="15f22-120">In caso contrario, il `Get-Help` cmdlet non è possibile trovare il file della Guida.</span><span class="sxs-lookup"><span data-stu-id="15f22-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="15f22-121">Non sono previsti requisiti tecnici per il nome di un file della Guida funzione.</span><span class="sxs-lookup"><span data-stu-id="15f22-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="15f22-122">Tuttavia, una procedura consigliata è assegnare un nome file della Guida per il modulo di script in cui la funzione è definita.</span><span class="sxs-lookup"><span data-stu-id="15f22-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="15f22-123">Ad esempio, la funzione seguente è definita nel file MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="15f22-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="15f22-124">File della Guida comandi CIM</span><span class="sxs-lookup"><span data-stu-id="15f22-124">CIM Command Help Files</span></span>

<span data-ttu-id="15f22-125">Il file della Guida per un comando CIM deve essere denominato per il file CDXML in cui è definito il comando CIM.</span><span class="sxs-lookup"><span data-stu-id="15f22-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="15f22-126">Usare il formato del nome file seguente:</span><span class="sxs-lookup"><span data-stu-id="15f22-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="15f22-127">I comandi CIM sono definiti nel file CDXML che possono essere inclusi nei moduli come i moduli annidati.</span><span class="sxs-lookup"><span data-stu-id="15f22-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="15f22-128">Quando il comando CIM viene importato nella sessione come una funzione, Windows PowerShell aggiunge un `.ExternalHelp` commento file di una parola chiave per la definizione di funzione che associa la funzione con un supporto XML è denominato per il file CDXML in cui è definito il comando CIM.</span><span class="sxs-lookup"><span data-stu-id="15f22-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="15f22-129">File della Guida del flusso di lavoro di script</span><span class="sxs-lookup"><span data-stu-id="15f22-129">Script Workflow Help Files</span></span>

<span data-ttu-id="15f22-130">I flussi di lavoro di script che sono inclusi nei moduli possono essere documentati nel file della Guida basati su XML.</span><span class="sxs-lookup"><span data-stu-id="15f22-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="15f22-131">Non sono previsti requisiti tecnici per il nome del file della Guida.</span><span class="sxs-lookup"><span data-stu-id="15f22-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="15f22-132">Tuttavia, una procedura consigliata è assegnare un nome file della Guida per il modulo di script in cui è definito il flusso di lavoro di script.</span><span class="sxs-lookup"><span data-stu-id="15f22-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="15f22-133">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="15f22-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="15f22-134">A differenza di altri comandi script, i flussi di lavoro di script non richiedono un `.ExternalHelp` commento parola chiave per associarle a un file della Guida.</span><span class="sxs-lookup"><span data-stu-id="15f22-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="15f22-135">Ma Windows PowerShell esegue la ricerca nelle sottodirectory specifiche di impostazioni cultura dell'interfaccia utente della directory del modulo per i file della Guida basati su XML e cerca la Guida per il flusso di lavoro di script in tutti i file.</span><span class="sxs-lookup"><span data-stu-id="15f22-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="15f22-136">`.ExternalHelp` parola chiave di commento vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="15f22-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="15f22-137">Poiché il `.ExternalHelp` parola chiave di commento viene ignorato, il `Get-Help` cmdlet potranno richiedere assistenza per i flussi di lavoro di script solo quando vengono inclusi nei moduli.</span><span class="sxs-lookup"><span data-stu-id="15f22-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>