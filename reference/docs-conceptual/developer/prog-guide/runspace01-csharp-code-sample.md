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
ms.openlocfilehash: 0978880a4294edb96fc6edb00f420cd0a9ad197b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977982"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="b02c6-102">Codice di esempio di Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="b02c6-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="b02c6-103">Ecco gli esempi di codice per spazio descritto in [creazione di un'applicazione console che esegue un comando specificato](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="b02c6-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="b02c6-104">A tale scopo, l'applicazione richiama un spazio e quindi richiama un comando.</span><span class="sxs-lookup"><span data-stu-id="b02c6-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="b02c6-105">Si noti che questa applicazione non specifica le informazioni di configurazione spazio né crea in modo esplicito una pipeline.</span><span class="sxs-lookup"><span data-stu-id="b02c6-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="b02c6-106">Il comando richiamato è il cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="b02c6-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="b02c6-107">È possibile scaricare il C# file di origine (runspace01.cs) per questo spazio utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="b02c6-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="b02c6-108">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="b02c6-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="b02c6-109">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="b02c6-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b02c6-110">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="b02c6-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="b02c6-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b02c6-111">See Also</span></span>

[<span data-ttu-id="b02c6-112">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b02c6-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b02c6-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b02c6-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
