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
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366480"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="42d6f-102">Codice di esempio di Runspace08</span><span class="sxs-lookup"><span data-stu-id="42d6f-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="42d6f-103">Ecco il codice sorgente per l'esempio Runspace08 descritto in [creazione di un'applicazione console che aggiunge parametri a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="42d6f-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="42d6f-104">Questa applicazione di esempio crea un spazio, crea una pipeline, aggiunge due comandi alla pipeline, aggiunge due parametri al secondo comando e quindi esegue la pipeline.</span><span class="sxs-lookup"><span data-stu-id="42d6f-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="42d6f-105">I comandi aggiunti alla pipeline sono i cmdlet `Get-Process` e `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="42d6f-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="42d6f-106">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="42d6f-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="42d6f-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="42d6f-107">See Also</span></span>

[<span data-ttu-id="42d6f-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="42d6f-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
