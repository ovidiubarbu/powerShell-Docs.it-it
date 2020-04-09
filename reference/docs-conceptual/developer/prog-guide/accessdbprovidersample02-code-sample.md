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
ms.openlocfilehash: 32abcfafb207ada23667cc6f0f03d382c6868ccb
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978610"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="5c718-102">Codice di esempio di AccessDbProviderSample02</span><span class="sxs-lookup"><span data-stu-id="5c718-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="5c718-103">Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5c718-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="5c718-104">Questa implementazione crea un percorso, effettua una connessione a un database di Access e quindi rimuove l'unità.</span><span class="sxs-lookup"><span data-stu-id="5c718-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="5c718-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider02.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="5c718-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5c718-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5c718-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5c718-107">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="5c718-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="5c718-108">Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5c718-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="5c718-109">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="5c718-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="5c718-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5c718-110">See Also</span></span>

[<span data-ttu-id="5c718-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c718-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5c718-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5c718-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
