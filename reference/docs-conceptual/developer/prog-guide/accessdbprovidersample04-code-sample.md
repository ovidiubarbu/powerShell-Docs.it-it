---
title: Esempio di codice AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366970"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="a3ffa-102">Codice di esempio di AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="a3ffa-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="a3ffa-103">Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a3ffa-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="a3ffa-104">Questo provider funziona in archivi dati a più livelli.</span><span class="sxs-lookup"><span data-stu-id="a3ffa-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="a3ffa-105">Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene definito nodo di elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="a3ffa-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="a3ffa-106">Consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire gerarchicamente con l'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="a3ffa-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a3ffa-107">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="a3ffa-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="a3ffa-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a3ffa-108">See Also</span></span>

[<span data-ttu-id="a3ffa-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a3ffa-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
