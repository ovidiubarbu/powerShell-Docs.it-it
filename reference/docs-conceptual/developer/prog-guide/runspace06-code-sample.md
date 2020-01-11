---
title: Esempio di codice RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 98b01a79474c58afc3ef1ae5b3761a8d651162f9
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870626"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="cc753-102">Codice di esempio di Runspace06</span><span class="sxs-lookup"><span data-stu-id="cc753-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="cc753-103">Ecco il codice sorgente per l'esempio Runspace06 descritto in [configurazione di un spazio mediante uno snap-in di Windows PowerShell](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="cc753-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="cc753-104">Questa applicazione di esempio crea un spazio basato su uno snap-in di Windows PowerShell, che viene quindi usato per eseguire una pipeline con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="cc753-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="cc753-105">A tale scopo, l'applicazione crea le informazioni di configurazione spazio, crea una spazio, crea una pipeline con un unico comando, quindi esegue la pipeline.</span><span class="sxs-lookup"><span data-stu-id="cc753-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="cc753-106">È possibile scaricare il C# file di origine (runspace06.cs) utilizzando Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc753-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="cc753-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="cc753-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="cc753-108">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="cc753-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cc753-109">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="cc753-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="cc753-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cc753-110">See Also</span></span>

[<span data-ttu-id="cc753-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc753-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="cc753-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cc753-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
