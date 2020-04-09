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
ms.openlocfilehash: 60f0ed4e3d39ee93ab63023161d09a6c7b914798
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978577"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="ed1cd-102">Codice di esempio di AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="ed1cd-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="ed1cd-103">Il codice seguente illustra l'implementazione del provider di Windows PowerShell descritto in [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ed1cd-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="ed1cd-104">Questo provider funziona in archivi dati a più livelli.</span><span class="sxs-lookup"><span data-stu-id="ed1cd-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="ed1cd-105">Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene definito nodo di elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="ed1cd-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="ed1cd-106">Consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire gerarchicamente con l'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="ed1cd-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ed1cd-107">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="ed1cd-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="ed1cd-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ed1cd-108">See Also</span></span>

[<span data-ttu-id="ed1cd-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ed1cd-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
