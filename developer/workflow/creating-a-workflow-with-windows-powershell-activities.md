---
title: Creazione di un flusso di lavoro con attività di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080445"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="424d7-102">Creazione di un flusso di lavoro con le attività di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="424d7-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="424d7-103">È possibile creare un flusso di lavoro di Windows PowerShell selezionando le attività dalla casella degli strumenti di Visual Studio e trascinarli nella finestra di progettazione del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="424d7-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="424d7-104">Per informazioni sull'aggiunta di attività di Windows PowerShell per Visual Studio Toolbox, vedere [aggiunta di attività di Windows PowerShell per Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="424d7-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="424d7-105">Le procedure seguenti descrivono come creare un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificato dall'utente, li aggiunge a un dominio se non sono già unite in join e quindi controlla di nuovo lo stato.</span><span class="sxs-lookup"><span data-stu-id="424d7-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="424d7-106">Impostazione del progetto</span><span class="sxs-lookup"><span data-stu-id="424d7-106">Setting up the Project</span></span>

1. <span data-ttu-id="424d7-107">Seguire la procedura descritta in [aggiunta di attività di Windows PowerShell per Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) per creare un progetto di flusso di lavoro e aggiungere le attività dalle [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e[ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) gli assembly nella casella degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="424d7-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="424d7-108">Aggiungere Automation, Microsoft.PowerShell.Activities, System. Management, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management per quanto riguarda il progetto come assembly di riferimento.</span><span class="sxs-lookup"><span data-stu-id="424d7-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="424d7-109">Aggiunta di attività al flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="424d7-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="424d7-110">Aggiungere un **sequenza** attività al flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="424d7-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="424d7-111">Creare un argomento denominato `ComputerName` con un argomento di tipo `String[]`.</span><span class="sxs-lookup"><span data-stu-id="424d7-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="424d7-112">Questo argomento rappresenta i nomi dei computer per controllare e creare un join.</span><span class="sxs-lookup"><span data-stu-id="424d7-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="424d7-113">Creare un argomento denominato `DomainCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="424d7-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="424d7-114">Questo argomento rappresenta le credenziali di dominio di un account di dominio che è autorizzato ad aggiungere un computer al dominio.</span><span class="sxs-lookup"><span data-stu-id="424d7-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="424d7-115">Creare un argomento denominato `MachineCred` typu [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="424d7-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="424d7-116">Questo argomento rappresenta le credenziali di amministratore sui computer per controllare e creare un join.</span><span class="sxs-lookup"><span data-stu-id="424d7-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="424d7-117">Aggiungere un **ParallelForEach** attività all'interno di **sequenza** attività.</span><span class="sxs-lookup"><span data-stu-id="424d7-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="424d7-118">Immettere `comp` e `ComputerName` nelle caselle di testo in modo che il ciclo scorre gli elementi del `ComputerName` matrice.</span><span class="sxs-lookup"><span data-stu-id="424d7-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="424d7-119">Aggiungere un **sequenza** il corpo dell'attività la **ParallelForEach** attività.</span><span class="sxs-lookup"><span data-stu-id="424d7-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="424d7-120">Impostare il **DisplayName** proprietà della sequenza `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="424d7-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="424d7-121">Aggiungere un **GetWmiObject** attività per il **JoinDomain** sequenza.</span><span class="sxs-lookup"><span data-stu-id="424d7-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="424d7-122">Modificare le proprietà del **GetWmiObject** attività come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="424d7-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="424d7-123">Proprietà</span><span class="sxs-lookup"><span data-stu-id="424d7-123">Property</span></span>|<span data-ttu-id="424d7-124">Value</span><span class="sxs-lookup"><span data-stu-id="424d7-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="424d7-125">**Classe**</span><span class="sxs-lookup"><span data-stu-id="424d7-125">**Class**</span></span>|<span data-ttu-id="424d7-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="424d7-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="424d7-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="424d7-127">**PSComputerName**</span></span>|<span data-ttu-id="424d7-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="424d7-128">{comp}</span></span>|
   |<span data-ttu-id="424d7-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="424d7-129">**PSCredential**</span></span>|<span data-ttu-id="424d7-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="424d7-130">MachineCred</span></span>|

9. <span data-ttu-id="424d7-131">Aggiungere un **AddComputer** attività per il **JoinDomain** sequenza dopo il **GetWmiObject** attività.</span><span class="sxs-lookup"><span data-stu-id="424d7-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="424d7-132">Modificare le proprietà del **AddComputer** attività come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="424d7-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="424d7-133">Proprietà</span><span class="sxs-lookup"><span data-stu-id="424d7-133">Property</span></span>|<span data-ttu-id="424d7-134">Value</span><span class="sxs-lookup"><span data-stu-id="424d7-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="424d7-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="424d7-135">**ComputerName**</span></span>|<span data-ttu-id="424d7-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="424d7-136">{comp}</span></span>|
    |<span data-ttu-id="424d7-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="424d7-137">**DomainCredential**</span></span>|<span data-ttu-id="424d7-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="424d7-138">DomainCred</span></span>|

11. <span data-ttu-id="424d7-139">Aggiungere un **RestartComputer** attività per il **JoinDomain** sequenza dopo il **AddComputer** attività.</span><span class="sxs-lookup"><span data-stu-id="424d7-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="424d7-140">Modificare le proprietà del **RestartComputer** attività come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="424d7-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="424d7-141">Proprietà</span><span class="sxs-lookup"><span data-stu-id="424d7-141">Property</span></span>|<span data-ttu-id="424d7-142">Value</span><span class="sxs-lookup"><span data-stu-id="424d7-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="424d7-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="424d7-143">**ComputerName**</span></span>|<span data-ttu-id="424d7-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="424d7-144">{comp}</span></span>|
    |<span data-ttu-id="424d7-145">**Credenziali**</span><span class="sxs-lookup"><span data-stu-id="424d7-145">**Credential**</span></span>|<span data-ttu-id="424d7-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="424d7-146">MachineCred</span></span>|
    |<span data-ttu-id="424d7-147">**per**</span><span class="sxs-lookup"><span data-stu-id="424d7-147">**For**</span></span>|<span data-ttu-id="424d7-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="424d7-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="424d7-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="424d7-149">**Force**</span></span>|<span data-ttu-id="424d7-150">True</span><span class="sxs-lookup"><span data-stu-id="424d7-150">True</span></span>|
    |<span data-ttu-id="424d7-151">Wait</span><span class="sxs-lookup"><span data-stu-id="424d7-151">Wait</span></span>|<span data-ttu-id="424d7-152">True</span><span class="sxs-lookup"><span data-stu-id="424d7-152">True</span></span>|
    |<span data-ttu-id="424d7-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="424d7-153">PSComputerName</span></span>|<span data-ttu-id="424d7-154">{""}</span><span class="sxs-lookup"><span data-stu-id="424d7-154">{""}</span></span>|

13. <span data-ttu-id="424d7-155">Aggiungere un **GetWmiObject** attività per il **JoinDomain** sequenza dopo il **RestartComputer** attività.</span><span class="sxs-lookup"><span data-stu-id="424d7-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="424d7-156">Modificare le proprietà per poter essere lo stesso come il precedente **GetWmiObject** attività.</span><span class="sxs-lookup"><span data-stu-id="424d7-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="424d7-157">Dopo avere completato le procedure, la finestra di progettazione del flusso di lavoro dovrebbe essere simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="424d7-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="424d7-158">![JoinDomain XAML nella finestra di progettazione del flusso di lavoro](../media/joindomainworkflow.png)
    ![JoinDomain XAML nella finestra di progettazione del flusso di lavoro](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="424d7-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>