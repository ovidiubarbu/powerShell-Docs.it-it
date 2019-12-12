---
title: Concetti di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366680"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="24172-102">Concetti di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="24172-103">Questa sezione contiene informazioni concettuali che consentono di comprendere PowerShell dal punto di vista di uno sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="24172-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="24172-104">Nome argomento</span><span class="sxs-lookup"><span data-stu-id="24172-104">Topic Name</span></span>|<span data-ttu-id="24172-105">Description</span><span class="sxs-lookup"><span data-stu-id="24172-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="24172-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="24172-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="24172-107">Descrizione degli oggetti di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24172-107">Description of PowerShell objects.</span></span> <span data-ttu-id="24172-108">Per ulteriori informazioni, vedere [informazioni sulla creazione di oggetti](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="24172-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="24172-109">Creazione di Runspaces</span><span class="sxs-lookup"><span data-stu-id="24172-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="24172-110">Ambienti operativi in cui vengono elaborati i comandi.</span><span class="sxs-lookup"><span data-stu-id="24172-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="24172-111">Per ulteriori informazioni, vedere la [classe spazio](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="24172-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="24172-112">Estensione di oggetti di output</span><span class="sxs-lookup"><span data-stu-id="24172-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="24172-113">Come estendere gli oggetti di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24172-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="24172-114">Per ulteriori informazioni, vedere [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="24172-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="24172-115">Registrazione di cmdlet</span><span class="sxs-lookup"><span data-stu-id="24172-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="24172-116">Come rendere disponibili i moduli e gli snap-in in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24172-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="24172-117">Per ulteriori informazioni, vedere [moduli e snap-](../cmdlet/modules-and-snap-ins.md)in.</span><span class="sxs-lookup"><span data-stu-id="24172-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="24172-118">Richiesta di conferma dai cmdlet</span><span class="sxs-lookup"><span data-stu-id="24172-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="24172-119">Come i cmdlet e i provider richiedono feedback da parte dell'utente prima che venga eseguita un'azione.</span><span class="sxs-lookup"><span data-stu-id="24172-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="24172-120">Classe RuntimeDefinedParameter</span><span class="sxs-lookup"><span data-stu-id="24172-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="24172-121">Dichiarazioni di parametri di Runtime.</span><span class="sxs-lookup"><span data-stu-id="24172-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="24172-122">Spazio dei nomi System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="24172-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="24172-123">Panoramica degli spazi dei nomi delle API di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24172-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="24172-124">Panoramica del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="24172-125">Panoramica sui provider PowerShell usati per accedere agli archivi dati.</span><span class="sxs-lookup"><span data-stu-id="24172-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="24172-126">Scrittura della Guida per i cmdlet di PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="24172-127">Come scrivere la guida per i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24172-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="24172-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24172-128">See also</span></span>

[<span data-ttu-id="24172-129">Classe PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="24172-130">Informazioni di riferimento sull'API PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="24172-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="24172-131">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="24172-132">Scrittura della Guida per i moduli di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="24172-133">Scrittura di un provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="24172-134">Informazioni di riferimento sulle API di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24172-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

<span data-ttu-id="24172-135">[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)</span><span class="sxs-lookup"><span data-stu-id="24172-135">[Windows PowerShell Reference](../windows-powershell-reference.md)</span></span>