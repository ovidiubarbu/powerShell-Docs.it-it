---
title: GetProc03 (C#) esempi di codice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 328f4eeea27243102679ab5d139181a878165ad6
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429755"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="e0aa1-102">Codice di esempio di GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0aa1-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="e0aa1-103">Il codice seguente viene illustrata l'implementazione di un `Get-Process` cmdlet in grado di accettare le pipeline di input.</span><span class="sxs-lookup"><span data-stu-id="e0aa1-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="e0aa1-104">Questa implementazione definisce una `Name` parametro che accetta l'input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi specificati e Usa quindi il [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodo come meccanismo di output per l'invio di oggetti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="e0aa1-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="e0aa1-105">È possibile scaricare il C# file di origine (getprov03.cs) per questo cmdlet Get-Process tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="e0aa1-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e0aa1-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e0aa1-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e0aa1-107">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="e0aa1-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e0aa1-108">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="e0aa1-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="e0aa1-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e0aa1-109">See Also</span></span>

[<span data-ttu-id="e0aa1-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0aa1-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e0aa1-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0aa1-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)