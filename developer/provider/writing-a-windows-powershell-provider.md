---
title: Scrittura di un Provider PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a54ce657-e0e0-4b3e-b9dc-aed39876f933
caps.latest.revision: 11
ms.openlocfilehash: 58252956184703fdcdb3aa9b1db617c6e91294c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080835"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="635c5-102">Scrittura di un provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="635c5-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="635c5-103">"La scrittura di un Provider di Windows PowerShell" è per i responsabili del programma che intendono progettare provider di Windows PowerShell e per gli sviluppatori che intendono implementare codice del provider.</span><span class="sxs-lookup"><span data-stu-id="635c5-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="635c5-104">Aiuterà a comprendere il funzionamento di provider di Windows PowerShell e viene fornito un codice di esempio che è possibile usare per avviare la progettazione o scrivere i propri provider.</span><span class="sxs-lookup"><span data-stu-id="635c5-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="635c5-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="635c5-105">In This Section</span></span>

<span data-ttu-id="635c5-106">[Avvio rapido di Provider di Windows PowerShell](./windows-powershell-provider-quickstart.md) codice di esempio e la procedura dettagliata di un provider di base.</span><span class="sxs-lookup"><span data-stu-id="635c5-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="635c5-107">[Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md) in questa sezione contiene argomenti che descrivono cosa sono i provider Windows PowerShell e sul relativo funzionamento.</span><span class="sxs-lookup"><span data-stu-id="635c5-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="635c5-108">[La scrittura di un provider di elementi](./writing-an-item-provider.md) codice di esempio e procedura dettagliata di metodi che supportano ottenendo e impostando gli elementi.</span><span class="sxs-lookup"><span data-stu-id="635c5-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="635c5-109">[Scrittura di un provider di contenitore](./writing-a-container-provider.md) codice di esempio e la procedura dettagliata di metodi che supportano i contenitori (gli elementi che hanno altri elementi come elementi figlio).</span><span class="sxs-lookup"><span data-stu-id="635c5-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="635c5-110">[Scrittura di un provider di navigazione](./writing-a-navigation-provider.md) codice di esempio e procedura dettagliata di metodi che supportano i contenitori nidificati, i percorsi relativi e spostamento di elementi da un percorso a un altro.</span><span class="sxs-lookup"><span data-stu-id="635c5-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="635c5-111">[Esempi di provider](./provider-samples.md) in questa sezione vengono forniti esempi di provider.</span><span class="sxs-lookup"><span data-stu-id="635c5-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="635c5-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="635c5-112">See Also</span></span>

[<span data-ttu-id="635c5-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="635c5-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)