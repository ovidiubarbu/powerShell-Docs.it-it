---
title: La scrittura di un flusso di lavoro di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080323"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="a45a8-102">Come scrivere un flusso di lavoro di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45a8-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="a45a8-103">È possibile creare un flusso di lavoro XAML mediante l'aggiunta di attività esposte dagli assembly di Windows PowerShell per la finestra di progettazione del flusso di lavoro in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a45a8-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="a45a8-104">Gli assembly seguenti di Windows PowerShell espongono le attività basate sul flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="a45a8-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a45a8-105">Se si desidera fornire la Guida per il flusso di lavoro, un flusso di lavoro XAML deve essere compresso come un modulo.</span><span class="sxs-lookup"><span data-stu-id="a45a8-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="a45a8-106">Per informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="a45a8-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="a45a8-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="a45a8-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="a45a8-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="a45a8-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="a45a8-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="a45a8-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="a45a8-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="a45a8-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="a45a8-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="a45a8-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="a45a8-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="a45a8-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="a45a8-113">Gli argomenti seguenti descrivono come creare un flusso di lavoro con attività di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a45a8-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="a45a8-114">Aggiunta di attività di Windows PowerShell nella casella degli strumenti di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a45a8-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="a45a8-115">Creazione di un flusso di lavoro con attività di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45a8-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="a45a8-116">Creazione di un flusso di lavoro usando uno Script di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45a8-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="a45a8-117">L'importazione e richiamare un flusso di lavoro di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45a8-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="a45a8-118">Creazione di un'attività flusso di lavoro da un Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a45a8-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)