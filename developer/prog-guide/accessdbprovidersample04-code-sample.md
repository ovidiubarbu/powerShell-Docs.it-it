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
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853607"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="54290-102">Codice di esempio di AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="54290-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="54290-103">Il codice seguente viene illustrata l'implementazione del provider di Windows PowerShell descritto nella [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="54290-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="54290-104">Questo provider funziona in archivi dati a più livelli.</span><span class="sxs-lookup"><span data-stu-id="54290-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="54290-105">Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene considerato come un nodo di elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="54290-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="54290-106">Tramite l'archivio dati, consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire in modo gerarchico.</span><span class="sxs-lookup"><span data-stu-id="54290-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="54290-107">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="54290-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="54290-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54290-108">See Also</span></span>

[<span data-ttu-id="54290-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="54290-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)