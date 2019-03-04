---
title: Esempio di codice RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 2b5ac097e8a52832b0f8cfb93b84eef56fc64858
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854597"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="d7baf-102">Codice di esempio di Runspace05</span><span class="sxs-lookup"><span data-stu-id="d7baf-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="d7baf-103">Ecco il codice sorgente dell'esempio Runspace05 descritto nella [configurazione di un RunspaceConfiguration usando spazio di esecuzione](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="d7baf-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="d7baf-104">In questo esempio viene illustrato come creare le informazioni di configurazione dello spazio di esecuzione, creare uno spazio di esecuzione, creare una pipeline con un singolo comando e quindi eseguire la pipeline.</span><span class="sxs-lookup"><span data-stu-id="d7baf-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="d7baf-105">Il comando che viene eseguito è il `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7baf-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d7baf-106">È possibile scaricare il C# file di origine (runspace05.cs) tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="d7baf-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d7baf-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d7baf-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="d7baf-108">È possibile scaricare il C# file di origine (runspace05.cs) tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="d7baf-108">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d7baf-109">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d7baf-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d7baf-110">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="d7baf-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d7baf-111">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="d7baf-111">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="d7baf-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d7baf-112">See Also</span></span>

[<span data-ttu-id="d7baf-113">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7baf-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d7baf-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d7baf-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)