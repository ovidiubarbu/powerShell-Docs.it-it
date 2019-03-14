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
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795607"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="da0f4-102">Codice di esempio di AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="da0f4-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="da0f4-103">Il codice seguente viene illustrata l'implementazione di provider di contenuti descritto in Windows PowerShell [creazione di un Provider di contenuti di Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="da0f4-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="da0f4-104">Questo provider consente all'utente di modificare il contenuto degli elementi in un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="da0f4-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="da0f4-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per il provider con il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="da0f4-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="da0f4-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="da0f4-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="da0f4-107">Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="da0f4-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="da0f4-108">Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="da0f4-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="da0f4-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="da0f4-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="da0f4-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="da0f4-110">See Also</span></span>

[<span data-ttu-id="da0f4-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da0f4-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="da0f4-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="da0f4-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)