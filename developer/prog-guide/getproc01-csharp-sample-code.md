---
title: GetProc01 (C#) esempi di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430078"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="23b11-102">Codice di esempio di GetProc01 (C#)</span><span class="sxs-lookup"><span data-stu-id="23b11-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="23b11-103">Il codice seguente illustra l'implementazione del cmdlet di esempio GetProc01.</span><span class="sxs-lookup"><span data-stu-id="23b11-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="23b11-104">Si noti che il cmdlet è semplificato dagli lasciando l'effettiva operazione di recupero di processo per il [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) (metodo).</span><span class="sxs-lookup"><span data-stu-id="23b11-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="23b11-105">È possibile scaricare il C# file di origine (getproc01.cs) per questo cmdlet Get-Process tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="23b11-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="23b11-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="23b11-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="23b11-107">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="23b11-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="23b11-108">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="23b11-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="23b11-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="23b11-109">See Also</span></span>

[<span data-ttu-id="23b11-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="23b11-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="23b11-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="23b11-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)