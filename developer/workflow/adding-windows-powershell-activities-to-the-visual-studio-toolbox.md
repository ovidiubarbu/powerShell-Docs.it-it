---
title: Aggiunta di Windows PowerShell attività alla casella degli strumenti di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863567"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="f7a73-102">Aggiunta di attività di Windows PowerShell nella casella degli strumenti di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7a73-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="f7a73-103">Prima di creare un flusso di lavoro di PowerShell usando Progettazione flussi di lavoro, è innanzitutto necessario aggiungere le attività di PowerShell nella casella degli strumenti in un progetto di applicazione console flusso di lavoro di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a73-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="f7a73-104">La procedura seguente viene illustrato come aggiungere le attività dall'assembly Microsoft.PowerShell.Core.Activities alla casella degli strumenti di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a73-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="f7a73-105">Aggiunta di attività di Windows PowerShell nella casella degli strumenti</span><span class="sxs-lookup"><span data-stu-id="f7a73-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="f7a73-106">Creare un nuovo progetto di applicazione console flusso di lavoro in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a73-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="f7a73-107">Nel **View** menu, fare clic su **della casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="f7a73-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="f7a73-108">Aggiungere una nuova scheda della casella degli strumenti facendo clic all'interno della casella degli strumenti e scegliendo **Aggiungi scheda**e assegnare un nome, ad esempio "Attività di PowerShell" la nuova scheda.</span><span class="sxs-lookup"><span data-stu-id="f7a73-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="f7a73-109">Aggiunta di una scheda consente di raggruppare le attività di PowerShell separata dagli altri strumenti della casella degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="f7a73-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="f7a73-110">Nella nuova scheda della casella degli strumenti, fare clic su **Scegli elementi...** . Il **Scegli elementi della casella degli strumenti** viene visualizzata la finestra.</span><span class="sxs-lookup"><span data-stu-id="f7a73-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="f7a73-111">Nel **Scegli elementi della casella degli strumenti** finestra di dialogo, fare clic sui **System. Activities** scheda.</span><span class="sxs-lookup"><span data-stu-id="f7a73-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="f7a73-112">Fare clic su **esplorare**.</span><span class="sxs-lookup"><span data-stu-id="f7a73-112">Click **Browse**.</span></span>

7. <span data-ttu-id="f7a73-113">Passare alla cartella %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e e fare doppio clic su Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="f7a73-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="f7a73-114">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7a73-114">Click **OK**.</span></span> <span data-ttu-id="f7a73-115">Le attività definite dall'assembly Microsoft.PowerShell.Core.Activities sono ora disponibili nella casella degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="f7a73-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7a73-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f7a73-116">See Also</span></span>

[<span data-ttu-id="f7a73-117">Come scrivere un flusso di lavoro di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7a73-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="f7a73-118">Creazione di un flusso di lavoro con attività di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7a73-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)