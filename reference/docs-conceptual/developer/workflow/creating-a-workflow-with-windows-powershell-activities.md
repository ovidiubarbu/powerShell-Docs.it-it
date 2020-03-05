---
title: Creazione di un flusso di lavoro con le attività di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 7d399786b9b43ee302493359d9702981045212e9
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78277466"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="21f24-102">Creazione di un flusso di lavoro con le attività di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="21f24-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="21f24-103">È possibile creare un flusso di lavoro di Windows PowerShell selezionando attività dalla casella degli strumenti di Visual Studio e trascinandoli nella finestra Progettazione flussi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="21f24-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="21f24-104">Per informazioni sull'aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio, vedere [aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="21f24-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="21f24-105">Nelle procedure riportate di seguito viene descritto come creare un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificati dall'utente, li aggiunge a un dominio se non sono già stati aggiunti, quindi controlla di nuovo lo stato.</span><span class="sxs-lookup"><span data-stu-id="21f24-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="21f24-106">Impostazione del progetto</span><span class="sxs-lookup"><span data-stu-id="21f24-106">Setting up the Project</span></span>

1. <span data-ttu-id="21f24-107">Per creare un progetto flusso di lavoro e aggiungere le attività dagli assembly [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) alla casella degli strumenti, seguire la procedura descritta in [aggiunta di attività di Windows PowerShell alla casella degli strumenti di Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) .</span><span class="sxs-lookup"><span data-stu-id="21f24-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="21f24-108">Aggiungere System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities e Microsoft. PowerShell. Commands. Management come al progetto come assembly di riferimento.</span><span class="sxs-lookup"><span data-stu-id="21f24-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="21f24-109">Aggiunta di attività al flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="21f24-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="21f24-110">Aggiungere un'attività **Sequence** al flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="21f24-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="21f24-111">Creare un argomento denominato `ComputerName` con un tipo di argomento `String[]`.</span><span class="sxs-lookup"><span data-stu-id="21f24-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="21f24-112">Questo argomento rappresenta i nomi dei computer da controllare e unire.</span><span class="sxs-lookup"><span data-stu-id="21f24-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="21f24-113">Creare un argomento denominato `DomainCred` di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="21f24-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="21f24-114">Questo argomento rappresenta le credenziali di dominio di un account di dominio autorizzato per l'aggiunta di un computer al dominio.</span><span class="sxs-lookup"><span data-stu-id="21f24-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="21f24-115">Creare un argomento denominato `MachineCred` di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="21f24-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="21f24-116">Questo argomento rappresenta le credenziali di un amministratore nei computer da controllare e unire.</span><span class="sxs-lookup"><span data-stu-id="21f24-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="21f24-117">Aggiungere un'attività **ActivityDesigner ParallelForEach** all'interno dell'attività **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="21f24-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="21f24-118">Immettere `comp` e `ComputerName` nelle caselle di testo in modo che il ciclo scorre gli elementi della matrice `ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="21f24-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="21f24-119">Aggiungere un'attività **Sequence** al corpo dell'attività **ActivityDesigner ParallelForEach** .</span><span class="sxs-lookup"><span data-stu-id="21f24-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="21f24-120">Impostare la proprietà **DisplayName** della sequenza su `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="21f24-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="21f24-121">Aggiungere un'attività **GetWmiObject** alla sequenza **JoinDomain** .</span><span class="sxs-lookup"><span data-stu-id="21f24-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="21f24-122">Modificare le proprietà dell'attività **GetWmiObject** come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="21f24-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="21f24-123">Proprietà</span><span class="sxs-lookup"><span data-stu-id="21f24-123">Property</span></span>|<span data-ttu-id="21f24-124">valore</span><span class="sxs-lookup"><span data-stu-id="21f24-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="21f24-125">**Class**</span><span class="sxs-lookup"><span data-stu-id="21f24-125">**Class**</span></span>|<span data-ttu-id="21f24-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="21f24-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="21f24-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="21f24-127">**PSComputerName**</span></span>|<span data-ttu-id="21f24-128">comp</span><span class="sxs-lookup"><span data-stu-id="21f24-128">{comp}</span></span>|
   |<span data-ttu-id="21f24-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="21f24-129">**PSCredential**</span></span>|<span data-ttu-id="21f24-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="21f24-130">MachineCred</span></span>|

9. <span data-ttu-id="21f24-131">Aggiungere un'attività **AddComputer** alla sequenza **JoinDomain** dopo l'attività **GetWmiObject** .</span><span class="sxs-lookup"><span data-stu-id="21f24-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="21f24-132">Modificare le proprietà dell'attività **AddComputer** come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="21f24-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="21f24-133">Proprietà</span><span class="sxs-lookup"><span data-stu-id="21f24-133">Property</span></span>|<span data-ttu-id="21f24-134">valore</span><span class="sxs-lookup"><span data-stu-id="21f24-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="21f24-135">**NomeComputer**</span><span class="sxs-lookup"><span data-stu-id="21f24-135">**ComputerName**</span></span>|<span data-ttu-id="21f24-136">comp</span><span class="sxs-lookup"><span data-stu-id="21f24-136">{comp}</span></span>|
    |<span data-ttu-id="21f24-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="21f24-137">**DomainCredential**</span></span>|<span data-ttu-id="21f24-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="21f24-138">DomainCred</span></span>|

11. <span data-ttu-id="21f24-139">Aggiungere un'attività **RestartComputer** alla sequenza **JoinDomain** dopo l'attività **AddComputer** .</span><span class="sxs-lookup"><span data-stu-id="21f24-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="21f24-140">Modificare le proprietà dell'attività **RestartComputer** come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="21f24-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="21f24-141">Proprietà</span><span class="sxs-lookup"><span data-stu-id="21f24-141">Property</span></span>|<span data-ttu-id="21f24-142">valore</span><span class="sxs-lookup"><span data-stu-id="21f24-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="21f24-143">**NomeComputer**</span><span class="sxs-lookup"><span data-stu-id="21f24-143">**ComputerName**</span></span>|<span data-ttu-id="21f24-144">comp</span><span class="sxs-lookup"><span data-stu-id="21f24-144">{comp}</span></span>|
    |<span data-ttu-id="21f24-145">**Credenziali**</span><span class="sxs-lookup"><span data-stu-id="21f24-145">**Credential**</span></span>|<span data-ttu-id="21f24-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="21f24-146">MachineCred</span></span>|
    |<span data-ttu-id="21f24-147">**Per**</span><span class="sxs-lookup"><span data-stu-id="21f24-147">**For**</span></span>|<span data-ttu-id="21f24-148">Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="21f24-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="21f24-149">**Forzare**</span><span class="sxs-lookup"><span data-stu-id="21f24-149">**Force**</span></span>|<span data-ttu-id="21f24-150">True</span><span class="sxs-lookup"><span data-stu-id="21f24-150">True</span></span>|
    |<span data-ttu-id="21f24-151">Attesa</span><span class="sxs-lookup"><span data-stu-id="21f24-151">Wait</span></span>|<span data-ttu-id="21f24-152">True</span><span class="sxs-lookup"><span data-stu-id="21f24-152">True</span></span>|
    |<span data-ttu-id="21f24-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="21f24-153">PSComputerName</span></span>|<span data-ttu-id="21f24-154">{""}</span><span class="sxs-lookup"><span data-stu-id="21f24-154">{""}</span></span>|

13. <span data-ttu-id="21f24-155">Aggiungere un'attività **GetWmiObject** alla sequenza **JoinDomain** dopo l'attività **RestartComputer** .</span><span class="sxs-lookup"><span data-stu-id="21f24-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="21f24-156">Modificare le proprietà in modo che corrispondano a quelle dell'attività **GetWmiObject** precedente.</span><span class="sxs-lookup"><span data-stu-id="21f24-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="21f24-157">Una volta completate le procedure, la finestra di progettazione del flusso di lavoro avrà un aspetto simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="21f24-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="21f24-158">![XAML JoinDomain in Progettazione flussi di lavoro](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
    ![XAML di JoinDomain in Progettazione flussi di lavoro](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="21f24-158">![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span></span>