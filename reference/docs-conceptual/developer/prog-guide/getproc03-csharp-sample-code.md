---
title: Codice diC#esempio GetProc03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 24f47ab8d99683e6d0024bd8073b6d7bb5dcbd90
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978373"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="e335d-102">Codice di esempio di GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="e335d-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="e335d-103">Nel codice seguente viene illustrata l'implementazione di un cmdlet di `Get-Process` che può accettare input da pipeline.</span><span class="sxs-lookup"><span data-stu-id="e335d-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="e335d-104">Questa implementazione definisce un parametro di `Name` che accetta input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi forniti, quindi usa il metodo [WriteObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) come meccanismo di output per l'invio di oggetti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="e335d-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="e335d-105">È possibile scaricare il C# file di origine (getprov03.cs) per questo cmdlet Get-proc utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e335d-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e335d-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e335d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e335d-107">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="e335d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e335d-108">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="e335d-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="e335d-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e335d-109">See Also</span></span>

[<span data-ttu-id="e335d-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e335d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e335d-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e335d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
