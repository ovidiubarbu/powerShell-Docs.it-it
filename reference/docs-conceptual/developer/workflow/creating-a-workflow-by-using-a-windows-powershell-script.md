---
title: Creazione di un flusso di lavoro tramite uno script di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366030"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="8835c-102">Creazione di un flusso di lavoro usando uno script di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8835c-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="8835c-103">È possibile creare un flusso di lavoro scrivendo uno script di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8835c-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="8835c-104">Per creare un flusso di lavoro, usare la parola chiave Workflow seguita da un nome per il flusso di lavoro prima del corpo dello script.</span><span class="sxs-lookup"><span data-stu-id="8835c-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="8835c-105">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="8835c-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="8835c-106">Il flusso di lavoro viene trovato in modo analogo a qualsiasi altro comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8835c-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="8835c-107">Implementazione di Parallel e Sequence</span><span class="sxs-lookup"><span data-stu-id="8835c-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="8835c-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supporta l'esecuzione di attività in parallelo.</span><span class="sxs-lookup"><span data-stu-id="8835c-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="8835c-109">Per implementare questa funzionalità in uno script di Windows PowerShell, usare la parola chiave `parallel` davanti a un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="8835c-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="8835c-110">È anche possibile usare la costruzione `foreach -parallel` per scorrere una raccolta di oggetti in parallelo.</span><span class="sxs-lookup"><span data-stu-id="8835c-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="8835c-111">Per eseguire un gruppo di attività in ordine sequenziale all'interno di un blocco parallelo, racchiudere il gruppo di attività in un blocco di script e precedere il blocco con la parola chiave Sequence.</span><span class="sxs-lookup"><span data-stu-id="8835c-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="8835c-112">Aggiunta di computer a un dominio</span><span class="sxs-lookup"><span data-stu-id="8835c-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="8835c-113">Lo script seguente crea un flusso di lavoro che controlla lo stato del dominio di un gruppo di computer specificati dall'utente, li aggiunge a un dominio se non sono già stati aggiunti, quindi controlla di nuovo lo stato.</span><span class="sxs-lookup"><span data-stu-id="8835c-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="8835c-114">Si tratta di una versione script del flusso di lavoro XAML illustrata in [creazione di un flusso di lavoro con le attività di Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="8835c-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```