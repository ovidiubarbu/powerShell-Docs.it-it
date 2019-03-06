---
title: GetProc04 codice di esempio (Visual Basic.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 8de99247574de130b91eea78b9af81dafbab48eb
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429619"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="7a7ab-102">Codice di esempio di GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="7a7ab-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="7a7ab-103">Il codice seguente viene illustrata l'implementazione di un `Get-Process` cmdlet che segnala gli errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="7a7ab-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="7a7ab-104">Questa implementazione chiama il [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo per segnalare gli errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="7a7ab-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="7a7ab-105">È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-Process tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="7a7ab-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7a7ab-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7a7ab-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7a7ab-107">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="7a7ab-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7a7ab-108">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="7a7ab-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="7a7ab-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a7ab-109">See Also</span></span>

[<span data-ttu-id="7a7ab-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a7ab-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7a7ab-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7a7ab-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)