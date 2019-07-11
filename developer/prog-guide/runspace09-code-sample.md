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
ms.openlocfilehash: 1a21af4b48a414d9c9fee57871eacb0a39c9ab11
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734902"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="8b351-102">Codice di esempio di Runspace09</span><span class="sxs-lookup"><span data-stu-id="8b351-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="8b351-103">Ecco il codice sorgente per l'esempio Runspace09 descritto in [la creazione di una Console dell'applicazione che richiama una Pipeline in modo asincrono](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="8b351-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="8b351-104">Questa applicazione di esempio crea e apre uno spazio di esecuzione, viene creata e richiama in modo asincrono una pipeline e quindi utilizza pipeline di eventi per elaborare lo script in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="8b351-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="8b351-105">Lo script che viene eseguito da questa applicazione crea i numeri interi compresi tra 1 e 10 in intervalli di 0,5 secondi (500 ms).</span><span class="sxs-lookup"><span data-stu-id="8b351-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="8b351-106">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="8b351-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="8b351-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8b351-107">See Also</span></span>

[<span data-ttu-id="8b351-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8b351-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)