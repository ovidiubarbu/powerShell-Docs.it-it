---
title: Esempio di codice RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 2e9cd80f1869e0d859187eea89eca414a84cb4ab
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870584"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="c7e37-102">Codice di esempio di Runspace08</span><span class="sxs-lookup"><span data-stu-id="c7e37-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="c7e37-103">Ecco il codice sorgente per l'esempio Runspace08 descritto in [creazione di un'applicazione console che aggiunge parametri a un comando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="c7e37-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="c7e37-104">Questa applicazione di esempio crea un spazio, crea una pipeline, aggiunge due comandi alla pipeline, aggiunge due parametri al secondo comando e quindi esegue la pipeline.</span><span class="sxs-lookup"><span data-stu-id="c7e37-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="c7e37-105">I comandi aggiunti alla pipeline sono i cmdlet `Get-Process` e `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="c7e37-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c7e37-106">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="c7e37-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="c7e37-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c7e37-107">See Also</span></span>

[<span data-ttu-id="c7e37-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c7e37-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
