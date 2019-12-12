---
title: Codice diC#esempio GetProc01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416166"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="816e2-102">Codice di esempio di GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="816e2-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="816e2-103">Nel codice seguente viene illustrata l'implementazione del cmdlet di esempio GetProc01.</span><span class="sxs-lookup"><span data-stu-id="816e2-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="816e2-104">Si noti che il cmdlet è semplificato lasciando il lavoro effettivo del recupero del processo al metodo [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) .</span><span class="sxs-lookup"><span data-stu-id="816e2-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="816e2-105">È possibile scaricare il C# file di origine (getproc01.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="816e2-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="816e2-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="816e2-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="816e2-107">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="816e2-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="816e2-108">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="816e2-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="816e2-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="816e2-109">See Also</span></span>

[<span data-ttu-id="816e2-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="816e2-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="816e2-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="816e2-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
