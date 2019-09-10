---
title: Esempio diC#codice RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848035"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="9601c-102">Codice di esempio di Runspace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="9601c-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="9601c-103">Ecco il C# codice sorgente per l'applicazione console descritta in "creazione di un'applicazione console che esegue uno script specificato".</span><span class="sxs-lookup"><span data-stu-id="9601c-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="9601c-104">Questo esempio usa la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) per eseguire uno script che recupera le informazioni sul processo usando l'elenco dei nomi di processo passati allo script.</span><span class="sxs-lookup"><span data-stu-id="9601c-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="9601c-105">Viene illustrato come passare gli oggetti di input a uno script e come recuperare gli oggetti Error, nonché gli oggetti di output.</span><span class="sxs-lookup"><span data-stu-id="9601c-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="9601c-106">È possibile scaricare il C# file di origine (runspace03.cs) per questo esempio utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="9601c-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9601c-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9601c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9601c-108">I file di origine scaricati sono disponibili nell'  **\<>** directory degli esempi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9601c-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9601c-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="9601c-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="9601c-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9601c-110">See Also</span></span>

[<span data-ttu-id="9601c-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9601c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9601c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9601c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)