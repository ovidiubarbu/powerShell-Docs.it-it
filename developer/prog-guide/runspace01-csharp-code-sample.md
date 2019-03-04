---
title: Runspace01 (C#) esempio di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 2f1839d1ba578cdfe97f60c741c84b0a57f1d8f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854217"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="53463-102">Codice di esempio di Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="53463-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="53463-103">Ecco gli esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="53463-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="53463-104">A tale scopo, l'applicazione richiama uno spazio di esecuzione e quindi richiama un comando.</span><span class="sxs-lookup"><span data-stu-id="53463-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="53463-105">Si noti che questa applicazione non specifica le informazioni di configurazione dello spazio di esecuzione, né e in modo esplicito crea una pipeline.</span><span class="sxs-lookup"><span data-stu-id="53463-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="53463-106">Il comando che viene richiamato il `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53463-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>
<span data-ttu-id="53463-107">Ecco gli esempi di codice per lo spazio di esecuzione descritto in [creazione di un'applicazione Console che avvia un comando specificato](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="53463-107">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="53463-108">A tale scopo, l'applicazione richiama uno spazio di esecuzione e quindi richiama un comando.</span><span class="sxs-lookup"><span data-stu-id="53463-108">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="53463-109">Si noti che questa applicazione non specifica le informazioni di configurazione dello spazio di esecuzione, né e in modo esplicito crea una pipeline.</span><span class="sxs-lookup"><span data-stu-id="53463-109">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="53463-110">Il comando che viene richiamato il `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53463-110">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="53463-111">È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio di esecuzione usando il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="53463-111">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="53463-112">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="53463-112">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="53463-113">È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio di esecuzione usando il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="53463-113">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="53463-114">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="53463-114">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="53463-115">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="53463-115">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="53463-116">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="53463-116">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="53463-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53463-117">See Also</span></span>

[<span data-ttu-id="53463-118">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="53463-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="53463-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="53463-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)