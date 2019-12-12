---
title: Codice di esempio GetProc04 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416101"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="e0f1d-102">Codice di esempio di GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="e0f1d-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="e0f1d-103">Nel codice seguente viene illustrata l'implementazione di un cmdlet di `Get-Process` che segnala errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="e0f1d-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="e0f1d-104">Questa implementazione chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) per segnalare errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="e0f1d-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="e0f1d-105">È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e0f1d-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e0f1d-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e0f1d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e0f1d-107">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="e0f1d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e0f1d-108">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="e0f1d-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="e0f1d-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e0f1d-109">See Also</span></span>

[<span data-ttu-id="e0f1d-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0f1d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e0f1d-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0f1d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
