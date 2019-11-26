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
ms.openlocfilehash: 7f75a3a3d2ab89696bb34ec2fdf7ba7a5ce0f9b1
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416230"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="e7dfc-102">Codice di esempio di AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="e7dfc-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="e7dfc-103">Il codice seguente illustra l'implementazione del provider di contenuti Windows PowerShell descritto in [creazione di un provider di contenuti Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e7dfc-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="e7dfc-104">Questo provider consente all'utente di modificare il contenuto degli elementi in un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="e7dfc-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="e7dfc-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7dfc-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e7dfc-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e7dfc-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e7dfc-107">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="e7dfc-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="e7dfc-108">Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e7dfc-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="e7dfc-109">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="e7dfc-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="e7dfc-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7dfc-110">See Also</span></span>

[<span data-ttu-id="e7dfc-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7dfc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e7dfc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e7dfc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
