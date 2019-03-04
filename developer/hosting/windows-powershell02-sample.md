---
title: Esempio PowerShell02 Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861067"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="d6955-102">Esempio di Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="d6955-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="d6955-103">Questo esempio viene illustrato come eseguire i comandi in modo asincrono utilizzando gli spazi di esecuzione di un pool di spazi di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d6955-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="d6955-104">L'esempio genera un elenco di comandi e quindi esegue i comandi, mentre il motore di Windows PowerShell apre uno spazio di esecuzione dal pool quando è necessaria.</span><span class="sxs-lookup"><span data-stu-id="d6955-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6955-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d6955-105">Requirements</span></span>

- <span data-ttu-id="d6955-106">Questo esempio richiede Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="d6955-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d6955-107">Illustra</span><span class="sxs-lookup"><span data-stu-id="d6955-107">Demonstrates</span></span>

<span data-ttu-id="d6955-108">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d6955-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="d6955-109">Creazione di un oggetto RunspacePool con un numero minimo e massimo di spazi di esecuzione possono essere aperte contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d6955-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="d6955-110">Creazione di un elenco dei comandi.</span><span class="sxs-lookup"><span data-stu-id="d6955-110">Creating a list of commands.</span></span>

- <span data-ttu-id="d6955-111">Eseguire i comandi in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="d6955-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="d6955-112">Chiama il [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) metodo per visualizzare il numero di spazi di esecuzione sono gratuiti.</span><span class="sxs-lookup"><span data-stu-id="d6955-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="d6955-113">Acquisire l'output del comando con il [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) (metodo).</span><span class="sxs-lookup"><span data-stu-id="d6955-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="d6955-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="d6955-114">Example</span></span>

<span data-ttu-id="d6955-115">In questo esempio illustra come aprire gli spazi di esecuzione di un pool di spazi di esecuzione e come eseguire in modo asincrono i comandi in questi spazi di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d6955-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="d6955-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d6955-116">See Also</span></span>

[<span data-ttu-id="d6955-117">Scrittura di un'applicazione Host di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="d6955-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)