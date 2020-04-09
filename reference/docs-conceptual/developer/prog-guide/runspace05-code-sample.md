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
ms.openlocfilehash: 4d9a2db76fe69a8509d33a22124f5f952b1d3c80
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978305"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="7a34e-102">Codice di esempio di Runspace05</span><span class="sxs-lookup"><span data-stu-id="7a34e-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="7a34e-103">Ecco il codice sorgente per l'esempio Runspace05 descritto in [configurazione di un spazio con RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="7a34e-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="7a34e-104">Questo esempio illustra come creare le informazioni di configurazione di spazio, creare un spazio, creare una pipeline con un unico comando e quindi eseguire la pipeline.</span><span class="sxs-lookup"><span data-stu-id="7a34e-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="7a34e-105">Il comando eseguito è il cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="7a34e-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="7a34e-106">È possibile scaricare il C# file di origine (runspace05.cs) utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="7a34e-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7a34e-107">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7a34e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="7a34e-108">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="7a34e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7a34e-109">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="7a34e-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="7a34e-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a34e-110">See Also</span></span>

[<span data-ttu-id="7a34e-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a34e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7a34e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7a34e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
