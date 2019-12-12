---
title: Parametri Quantity | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369560"
---
# <a name="quantity-parameters"></a><span data-ttu-id="25784-102">Parametri delle quantità</span><span class="sxs-lookup"><span data-stu-id="25784-102">Quantity Parameters</span></span>

<span data-ttu-id="25784-103">Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri di quantità.</span><span class="sxs-lookup"><span data-stu-id="25784-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="25784-104">Parametro</span><span class="sxs-lookup"><span data-stu-id="25784-104">Parameter</span></span>|<span data-ttu-id="25784-105">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="25784-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="25784-106">**Tutto**</span><span class="sxs-lookup"><span data-stu-id="25784-106">**All**</span></span><br><span data-ttu-id="25784-107">Tipo di dati: Boolean</span><span class="sxs-lookup"><span data-stu-id="25784-107">Data type: Boolean</span></span>|<span data-ttu-id="25784-108">Implementare questo parametro in modo che `true` indichi che è necessario agire su tutte le risorse anziché su un subset predefinito di risorse.</span><span class="sxs-lookup"><span data-stu-id="25784-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="25784-109">Implementare questo parametro in modo che `false` indichi un subset delle risorse.</span><span class="sxs-lookup"><span data-stu-id="25784-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="25784-110">**Allocation**</span><span class="sxs-lookup"><span data-stu-id="25784-110">**Allocation**</span></span><br><span data-ttu-id="25784-111">Tipo di dati: Int32</span><span class="sxs-lookup"><span data-stu-id="25784-111">Data type: Int32</span></span>|<span data-ttu-id="25784-112">Implementare questo parametro in modo che l'utente possa specificare il numero di elementi da allocare.</span><span class="sxs-lookup"><span data-stu-id="25784-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="25784-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="25784-113">**BlockCount**</span></span><br><span data-ttu-id="25784-114">Tipo di dati: Int64</span><span class="sxs-lookup"><span data-stu-id="25784-114">Data type: Int64</span></span>|<span data-ttu-id="25784-115">Implementare questo parametro in modo che l'utente possa specificare il numero di blocchi.</span><span class="sxs-lookup"><span data-stu-id="25784-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="25784-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="25784-116">**Count**</span></span><br><span data-ttu-id="25784-117">Tipo di dati: Int64</span><span class="sxs-lookup"><span data-stu-id="25784-117">Data type: Int64</span></span>|<span data-ttu-id="25784-118">Implementare questo parametro in modo che l'utente possa specificare il conteggio.</span><span class="sxs-lookup"><span data-stu-id="25784-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="25784-119">**Ambito**</span><span class="sxs-lookup"><span data-stu-id="25784-119">**Scope**</span></span><br><span data-ttu-id="25784-120">Tipo di dati: parola chiave</span><span class="sxs-lookup"><span data-stu-id="25784-120">Data type: Keyword</span></span>|<span data-ttu-id="25784-121">Implementare questo parametro in modo che l'utente possa specificare l'ambito su cui operare.</span><span class="sxs-lookup"><span data-stu-id="25784-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="25784-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25784-122">See Also</span></span>

[<span data-ttu-id="25784-123">Parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="25784-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="25784-124">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25784-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="25784-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="25784-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
