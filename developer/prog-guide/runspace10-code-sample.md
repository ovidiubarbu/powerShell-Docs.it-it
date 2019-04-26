---
title: Esempio di codice RunSpace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081241"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="3bc55-102">Codice di esempio di Runspace10</span><span class="sxs-lookup"><span data-stu-id="3bc55-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="3bc55-103">Ecco il codice sorgente dell'esempio Runspace10.</span><span class="sxs-lookup"><span data-stu-id="3bc55-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="3bc55-104">Questa applicazione di esempio aggiunge un cmdlet per [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) e quindi Usa le informazioni di configurazione modificato per creare lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="3bc55-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="3bc55-105">È possibile scaricare il C# file di origine (runspace10.cs) utilizzando il Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="3bc55-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3bc55-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3bc55-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3bc55-107">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="3bc55-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3bc55-108">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="3bc55-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="3bc55-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3bc55-109">See Also</span></span>

[<span data-ttu-id="3bc55-110">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bc55-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3bc55-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3bc55-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)