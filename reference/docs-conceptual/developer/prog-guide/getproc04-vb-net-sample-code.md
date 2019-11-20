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
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360300"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="81178-102">Codice di esempio di GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="81178-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="81178-103">Nel codice seguente viene illustrata l'implementazione di un cmdlet `Get-Process` che segnala errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="81178-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="81178-104">Questa implementazione chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) per segnalare errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="81178-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="81178-105">È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="81178-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="81178-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="81178-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="81178-107">I file di origine scaricati sono disponibili nella directory degli **esempi \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="81178-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="81178-108">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="81178-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="81178-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="81178-109">See Also</span></span>

[<span data-ttu-id="81178-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="81178-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="81178-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="81178-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)