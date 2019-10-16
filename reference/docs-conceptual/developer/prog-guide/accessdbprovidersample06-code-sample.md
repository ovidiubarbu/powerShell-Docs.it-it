---
title: Esempio di codice AccessDbProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 90927917550ade695f32c6f763f8cc4a8b347275
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366940"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="22b41-102">Codice di esempio di AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="22b41-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="22b41-103">Il codice seguente illustra l'implementazione del provider di contenuti Windows PowerShell descritto in [creazione di un provider di contenuti Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="22b41-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="22b41-104">Questo provider consente all'utente di modificare il contenuto degli elementi in un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="22b41-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="22b41-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="22b41-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="22b41-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="22b41-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="22b41-107">I file di origine scaricati sono disponibili nella directory degli **esempi \<PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="22b41-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="22b41-108">Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="22b41-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="22b41-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="22b41-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="22b41-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="22b41-110">See Also</span></span>

[<span data-ttu-id="22b41-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="22b41-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="22b41-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="22b41-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
