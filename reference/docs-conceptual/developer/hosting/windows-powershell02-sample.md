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
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978645"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="cd386-102">Esempio di Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="cd386-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="cd386-103">Questo esempio illustra come eseguire i comandi in modo asincrono usando il Runspaces di un pool di spazio.</span><span class="sxs-lookup"><span data-stu-id="cd386-103">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="cd386-104">L'esempio genera un elenco di comandi, quindi esegue i comandi mentre il motore di Windows PowerShell apre un spazio dal pool quando necessario.</span><span class="sxs-lookup"><span data-stu-id="cd386-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd386-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="cd386-105">Requirements</span></span>

- <span data-ttu-id="cd386-106">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="cd386-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cd386-107">Dimostra</span><span class="sxs-lookup"><span data-stu-id="cd386-107">Demonstrates</span></span>

<span data-ttu-id="cd386-108">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="cd386-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="cd386-109">Creazione di un oggetto RunspacePool con un numero minimo e massimo di Runspaces consentiti per l'apertura nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="cd386-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="cd386-110">Creazione di un elenco di comandi.</span><span class="sxs-lookup"><span data-stu-id="cd386-110">Creating a list of commands.</span></span>
- <span data-ttu-id="cd386-111">Esecuzione dei comandi in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="cd386-111">Running the commands asynchronously.</span></span>
- <span data-ttu-id="cd386-112">Chiamata del metodo [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) per verificare il numero di Runspaces disponibili.</span><span class="sxs-lookup"><span data-stu-id="cd386-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="cd386-113">Acquisizione dell'output del comando con il metodo [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="cd386-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="cd386-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="cd386-114">Example</span></span>

<span data-ttu-id="cd386-115">Questo esempio illustra come aprire il Runspaces di un pool spazio e come eseguire i comandi in modo asincrono in tali Runspaces.</span><span class="sxs-lookup"><span data-stu-id="cd386-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="cd386-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cd386-116">See Also</span></span>

[<span data-ttu-id="cd386-117">Scrittura di un'applicazione host di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd386-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
