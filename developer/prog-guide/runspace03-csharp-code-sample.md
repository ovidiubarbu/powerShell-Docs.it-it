---
title: RunSpace03 (C#) esempio di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: e1fc91174a959d6acc306330afb8d5c2e7a9a860
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734994"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="597e1-102">Codice di esempio di Runspace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="597e1-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="597e1-103">Di seguito è riportato il C# codice sorgente per l'applicazione console descritto in [creazione di un'applicazione Console che avvia uno Script specificato](fd).</span><span class="sxs-lookup"><span data-stu-id="597e1-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](fd).</span></span> <span data-ttu-id="597e1-104">Questo esempio Usa la [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe per eseguire uno script che recupera elabora le informazioni usando l'elenco di nomi di processo, passata allo script.</span><span class="sxs-lookup"><span data-stu-id="597e1-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="597e1-105">Mostra come passare oggetti di input a uno script e come recuperare gli oggetti di errore, nonché gli oggetti di output.</span><span class="sxs-lookup"><span data-stu-id="597e1-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="597e1-106">È possibile scaricare il C# file di origine (runspace03.cs) per questo esempio di uso di Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="597e1-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="597e1-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="597e1-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="597e1-108">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="597e1-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="597e1-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="597e1-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="597e1-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="597e1-110">See Also</span></span>

[<span data-ttu-id="597e1-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="597e1-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="597e1-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="597e1-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)