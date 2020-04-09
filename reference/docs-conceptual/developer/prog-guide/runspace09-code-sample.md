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
ms.openlocfilehash: d7fa39485eea833483682c91c96417a76e5d770f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977540"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="275c5-102">Codice di esempio di Runspace09</span><span class="sxs-lookup"><span data-stu-id="275c5-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="275c5-103">Ecco il codice sorgente per l'esempio Runspace09 descritto in [creazione di un'applicazione console che richiama una pipeline in modo asincrono](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="275c5-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="275c5-104">Questa applicazione di esempio crea e apre un spazio, crea e richiama in modo asincrono una pipeline, quindi usa gli eventi della pipeline per elaborare lo script in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="275c5-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="275c5-105">Lo script eseguito da questa applicazione crea i numeri interi da 1 a 10 in intervalli di 0,5 secondi (500 ms).</span><span class="sxs-lookup"><span data-stu-id="275c5-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="275c5-106">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="275c5-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="275c5-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="275c5-107">See Also</span></span>

[<span data-ttu-id="275c5-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="275c5-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
