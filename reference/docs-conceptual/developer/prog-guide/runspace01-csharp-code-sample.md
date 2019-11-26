---
title: Esempio diC#codice Runspace01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 607113ed566fc1e08e5b1d7092c83da2a22366ca
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418012"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="ab5e9-102">Codice di esempio di Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="ab5e9-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="ab5e9-103">Ecco gli esempi di codice per spazio descritto in [creazione di un'applicazione console che esegue un comando specificato](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="ab5e9-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="ab5e9-104">A tale scopo, l'applicazione richiama un spazio e quindi richiama un comando.</span><span class="sxs-lookup"><span data-stu-id="ab5e9-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="ab5e9-105">Si noti che questa applicazione non specifica le informazioni di configurazione spazio né crea in modo esplicito una pipeline.</span><span class="sxs-lookup"><span data-stu-id="ab5e9-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="ab5e9-106">Il comando richiamato è il cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="ab5e9-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="ab5e9-107">È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="ab5e9-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ab5e9-108">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ab5e9-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ab5e9-109">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="ab5e9-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ab5e9-110">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="ab5e9-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="ab5e9-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ab5e9-111">See Also</span></span>

[<span data-ttu-id="ab5e9-112">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab5e9-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ab5e9-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ab5e9-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
