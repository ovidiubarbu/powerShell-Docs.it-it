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
ms.openlocfilehash: 2798e8b542b2f06247955409118e75c5652b644c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860787"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="2dbe9-102">Codice di esempio di AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="2dbe9-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="2dbe9-103">Il codice seguente viene illustrata l'implementazione di provider di contenuti descritto in Windows PowerShell [creazione di un Provider di contenuti di Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2dbe9-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="2dbe9-104">Questo provider consente all'utente di modificare il contenuto degli elementi in un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="2dbe9-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per il provider con il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2dbe9-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2dbe9-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2dbe9-107">È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per il provider con il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-107">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2dbe9-108">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2dbe9-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2dbe9-109">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="2dbe9-110">Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2dbe9-110">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="2dbe9-111">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="2dbe9-111">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="2dbe9-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2dbe9-112">See Also</span></span>

[<span data-ttu-id="2dbe9-113">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dbe9-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2dbe9-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2dbe9-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)