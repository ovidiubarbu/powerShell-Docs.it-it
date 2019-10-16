---
title: Esempi di codice GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360320"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="27fd2-102">Codici di esempio di GetProc04</span><span class="sxs-lookup"><span data-stu-id="27fd2-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="27fd2-103">Ecco gli esempi di codice per il cmdlet di esempio GetProc04.</span><span class="sxs-lookup"><span data-stu-id="27fd2-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="27fd2-104">Questo è l'esempio di cmdlet `Get-Process` descritto in [aggiunta della segnalazione errori non fatale al cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="27fd2-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="27fd2-105">Questo cmdlet `Get-Process` chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ogni volta che viene generata un'eccezione di operazione non valida durante il recupero delle informazioni sul processo.</span><span class="sxs-lookup"><span data-stu-id="27fd2-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="27fd2-106">È possibile scaricare il C# file di origine (getprov04.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="27fd2-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="27fd2-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="27fd2-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="27fd2-108">I file di origine scaricati sono disponibili nella directory degli **esempi \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="27fd2-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="27fd2-109">Per il codice di esempio completo, vedere gli argomenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="27fd2-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="27fd2-110">Linguaggio</span><span class="sxs-lookup"><span data-stu-id="27fd2-110">Language</span></span>|<span data-ttu-id="27fd2-111">Argomento</span><span class="sxs-lookup"><span data-stu-id="27fd2-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="27fd2-112">C#</span><span class="sxs-lookup"><span data-stu-id="27fd2-112">C#</span></span>|[<span data-ttu-id="27fd2-113">Codice diC#esempio GetProc04 ()</span><span class="sxs-lookup"><span data-stu-id="27fd2-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="27fd2-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="27fd2-114">VB.NET</span></span>|[<span data-ttu-id="27fd2-115">Codice di esempio GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="27fd2-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="27fd2-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="27fd2-116">See Also</span></span>

[<span data-ttu-id="27fd2-117">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="27fd2-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="27fd2-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="27fd2-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)