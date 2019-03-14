---
title: Esempio di codice AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795488"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="c6b21-102">Codice di esempio di AccessDbProviderSample02</span><span class="sxs-lookup"><span data-stu-id="c6b21-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="c6b21-103">Il codice seguente viene illustrata l'implementazione del provider di Windows PowerShell descritto nella [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c6b21-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="c6b21-104">Questa implementazione viene creato un percorso, stabilisce una connessione a un database di Access e quindi rimuove l'unità.</span><span class="sxs-lookup"><span data-stu-id="c6b21-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b21-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider02.cs) per questo provider tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6b21-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c6b21-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="c6b21-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c6b21-107">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="c6b21-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="c6b21-108">Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c6b21-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="c6b21-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="c6b21-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="c6b21-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c6b21-110">See Also</span></span>

[<span data-ttu-id="c6b21-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6b21-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c6b21-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c6b21-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)