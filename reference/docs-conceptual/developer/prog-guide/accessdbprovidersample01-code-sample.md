---
title: Esempio di codice AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: b52882c3f38b64347b9e9f2c3dedcc8a7dd02458
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978595"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="8fce6-102">Codice di esempio di AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="8fce6-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="8fce6-103">Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di base di Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8fce6-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="8fce6-104">Questa implementazione fornisce metodi per l'avvio e l'arresto del provider e anche se non fornisce un mezzo per accedere a un archivio dati o per ottenere o impostare i dati nell'archivio dati, fornisce le funzionalità di base richieste da tutti i provider.</span><span class="sxs-lookup"><span data-stu-id="8fce6-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="8fce6-105">È possibile scaricare il C# file di origine (AccessDBSampleProvider01.cs) per questo provider utilizzando Windows Software Development Kit per i componenti di runtime di Windows Vista e Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="8fce6-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8fce6-106">Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="8fce6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="8fce6-107">I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .</span><span class="sxs-lookup"><span data-stu-id="8fce6-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="8fce6-108">Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8fce6-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="8fce6-109">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="8fce6-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="8fce6-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8fce6-110">See Also</span></span>

[<span data-ttu-id="8fce6-111">Guida per programmatori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fce6-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8fce6-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8fce6-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
