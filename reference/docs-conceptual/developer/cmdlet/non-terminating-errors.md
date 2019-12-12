---
title: Errori non fatali | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369600"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="cb67e-102">Errori non irreversibili</span><span class="sxs-lookup"><span data-stu-id="cb67e-102">Non-Terminating Errors</span></span>

<span data-ttu-id="cb67e-103">In questo argomento viene illustrato il metodo utilizzato per segnalare errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="cb67e-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="cb67e-104">Viene inoltre illustrato come chiamare il metodo dall'interno del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb67e-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="cb67e-105">Quando si verifica un errore non fatale, il cmdlet deve segnalare l'errore chiamando il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) .</span><span class="sxs-lookup"><span data-stu-id="cb67e-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="cb67e-106">Quando il cmdlet segnala un errore non fatale, il cmdlet può continuare a operare su questo oggetto di input e su altri oggetti pipeline in ingresso.</span><span class="sxs-lookup"><span data-stu-id="cb67e-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="cb67e-107">Se il cmdlet chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , il cmdlet può scrivere un record di errore che descrive la condizione che ha causato l'errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="cb67e-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="cb67e-108">Per ulteriori informazioni sui record degli errori, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="cb67e-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="cb67e-109">I cmdlet possono chiamare [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) in base alle esigenze all'interno dei metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="cb67e-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="cb67e-110">Tuttavia, i cmdlet possono chiamare [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo dal thread che ha chiamato il [Metodo System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)o [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input.</span><span class="sxs-lookup"><span data-stu-id="cb67e-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="cb67e-111">Non chiamare [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) da un altro thread.</span><span class="sxs-lookup"><span data-stu-id="cb67e-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="cb67e-112">Comunicare invece gli errori al thread principale.</span><span class="sxs-lookup"><span data-stu-id="cb67e-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb67e-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cb67e-113">See Also</span></span>

[<span data-ttu-id="cb67e-114">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="cb67e-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="cb67e-115">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="cb67e-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="cb67e-116">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="cb67e-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="cb67e-117">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="cb67e-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="cb67e-118">Record degli errori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb67e-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="cb67e-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb67e-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
