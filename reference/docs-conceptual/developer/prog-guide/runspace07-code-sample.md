---
title: Esempio di codice RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: b3c2e70d534e8a267b35ae1715bd24277267e0d8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417896"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="0c060-102">Codice di esempio di Runspace07</span><span class="sxs-lookup"><span data-stu-id="0c060-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="0c060-103">Ecco il codice sorgente per l'esempio Runspace07 descritto in [creazione di un'applicazione console che aggiunge comandi a una pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="0c060-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="0c060-104">Questa applicazione di esempio crea un spazio, crea una pipeline, aggiunge due comandi alla pipeline e quindi esegue la pipeline.</span><span class="sxs-lookup"><span data-stu-id="0c060-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="0c060-105">I comandi aggiunti alla pipeline sono i cmdlet `Get-Process` e `Measure-Object`.</span><span class="sxs-lookup"><span data-stu-id="0c060-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="0c060-106">È possibile scaricare il C# file di origine (runspace07.cs) utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="0c060-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0c060-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0c060-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0c060-108">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="0c060-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0c060-109">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="0c060-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="0c060-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0c060-110">See Also</span></span>

[<span data-ttu-id="0c060-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c060-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0c060-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0c060-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
