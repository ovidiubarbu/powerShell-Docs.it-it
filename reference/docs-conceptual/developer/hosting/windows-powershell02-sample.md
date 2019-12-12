---
title: Esempio di Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367300"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="1ce61-102">Esempio di Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="1ce61-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="1ce61-103">Questo esempio illustra come eseguire i comandi in modo asincrono usando il Runspaces di un pool di spazio.</span><span class="sxs-lookup"><span data-stu-id="1ce61-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="1ce61-104">L'esempio genera un elenco di comandi, quindi esegue i comandi mentre il motore di Windows PowerShell apre un spazio dal pool quando necessario.</span><span class="sxs-lookup"><span data-stu-id="1ce61-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ce61-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1ce61-105">Requirements</span></span>

- <span data-ttu-id="1ce61-106">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="1ce61-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1ce61-107">Illustra</span><span class="sxs-lookup"><span data-stu-id="1ce61-107">Demonstrates</span></span>

<span data-ttu-id="1ce61-108">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="1ce61-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="1ce61-109">Creazione di un oggetto RunspacePool con un numero minimo e massimo di Runspaces consentiti per l'apertura nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="1ce61-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="1ce61-110">Creazione di un elenco di comandi.</span><span class="sxs-lookup"><span data-stu-id="1ce61-110">Creating a list of commands.</span></span>

- <span data-ttu-id="1ce61-111">Esecuzione dei comandi in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="1ce61-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="1ce61-112">Chiamata del metodo [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) per verificare il numero di Runspaces disponibili.</span><span class="sxs-lookup"><span data-stu-id="1ce61-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="1ce61-113">Acquisizione dell'output del comando con il metodo [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="1ce61-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="1ce61-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ce61-114">Example</span></span>

<span data-ttu-id="1ce61-115">Questo esempio illustra come aprire il Runspaces di un pool spazio e come eseguire i comandi in modo asincrono in tali Runspaces.</span><span class="sxs-lookup"><span data-stu-id="1ce61-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="1ce61-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1ce61-116">See Also</span></span>

[<span data-ttu-id="1ce61-117">Scrittura di un'applicazione host di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ce61-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
