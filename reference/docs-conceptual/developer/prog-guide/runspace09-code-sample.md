---
title: Esempio di codice RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360130"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="a7ef4-102">Codice di esempio di Runspace09</span><span class="sxs-lookup"><span data-stu-id="a7ef4-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="a7ef4-103">Ecco il codice sorgente per l'esempio Runspace09 descritto in [creazione di un'applicazione console che richiama una pipeline in modo asincrono](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="a7ef4-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="a7ef4-104">Questa applicazione di esempio crea e apre un spazio, crea e richiama in modo asincrono una pipeline, quindi usa gli eventi della pipeline per elaborare lo script in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="a7ef4-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="a7ef4-105">Lo script eseguito da questa applicazione crea i numeri interi da 1 a 10 in intervalli di 0,5 secondi (500 ms).</span><span class="sxs-lookup"><span data-stu-id="a7ef4-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="a7ef4-106">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="a7ef4-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="a7ef4-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a7ef4-107">See Also</span></span>

[<span data-ttu-id="a7ef4-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a7ef4-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
