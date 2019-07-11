---
title: Esempio di codice RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734965"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="01003-102">Codice di esempio di Runspace05</span><span class="sxs-lookup"><span data-stu-id="01003-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="01003-103">Ecco il codice sorgente dell'esempio Runspace05 descritto nella [configurazione di un RunspaceConfiguration usando spazio di esecuzione](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="01003-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="01003-104">In questo esempio viene illustrato come creare le informazioni di configurazione dello spazio di esecuzione, creare uno spazio di esecuzione, creare una pipeline con un singolo comando e quindi eseguire la pipeline.</span><span class="sxs-lookup"><span data-stu-id="01003-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="01003-105">Il comando che viene eseguito è il `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01003-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="01003-106">È possibile scaricare il C# file di origine (runspace05.cs) tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="01003-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="01003-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="01003-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="01003-108">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="01003-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="01003-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="01003-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="01003-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="01003-110">See Also</span></span>

[<span data-ttu-id="01003-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="01003-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="01003-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="01003-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)