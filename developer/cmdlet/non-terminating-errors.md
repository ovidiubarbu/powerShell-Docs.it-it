---
title: Gli errori non è definitiva | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067655"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="eaad1-102">Errori non irreversibili</span><span class="sxs-lookup"><span data-stu-id="eaad1-102">Non-Terminating Errors</span></span>

<span data-ttu-id="eaad1-103">In questo argomento illustra il metodo utilizzato per segnalare errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="eaad1-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="eaad1-104">Inoltre illustrato come chiamare il metodo dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eaad1-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="eaad1-105">Quando si verifica un errore non irreversibile, il cmdlet deve segnalare l'errore chiamando il [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (metodo).</span><span class="sxs-lookup"><span data-stu-id="eaad1-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="eaad1-106">Quando il cmdlet segnala un errore non irreversibile, il cmdlet può continuare a funzionare su questo oggetto di input e in entrata ulteriormente gli oggetti di pipeline.</span><span class="sxs-lookup"><span data-stu-id="eaad1-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="eaad1-107">Se viene chiamato il cmdlet di [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo, il cmdlet può scrivere un record di errore che descrive la condizione che ha causato l'errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="eaad1-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="eaad1-108">Per altre informazioni sui record di errore, vedere [record di errore di Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="eaad1-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="eaad1-109">I cmdlet è possono chiamare [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) esigenze da entro i metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="eaad1-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="eaad1-110">Tuttavia, è possono chiamare i cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo dal thread che ha chiamato la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oppure [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo di elaborazione di input.</span><span class="sxs-lookup"><span data-stu-id="eaad1-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="eaad1-111">Non chiamare [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) da un altro thread.</span><span class="sxs-lookup"><span data-stu-id="eaad1-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="eaad1-112">Al contrario, comunicare gli errori nel thread principale.</span><span class="sxs-lookup"><span data-stu-id="eaad1-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="eaad1-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eaad1-113">See Also</span></span>

[<span data-ttu-id="eaad1-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="eaad1-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="eaad1-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="eaad1-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="eaad1-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="eaad1-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="eaad1-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="eaad1-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="eaad1-118">Record degli errori di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="eaad1-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="eaad1-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eaad1-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
