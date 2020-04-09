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
ms.openlocfilehash: 21d7c4fe69e5026089676c43ad69a4263732cc34
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978254"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="1023b-102">Codice di esempio di Runspace08</span><span class="sxs-lookup"><span data-stu-id="1023b-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="1023b-103">Ecco il codice sorgente per l'esempio Runspace08 descritto in [creazione di un'applicazione console che aggiunge parametri a un comando](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="1023b-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="1023b-104">Questa applicazione di esempio crea un spazio, crea una pipeline, aggiunge due comandi alla pipeline, aggiunge due parametri al secondo comando e quindi esegue la pipeline.</span><span class="sxs-lookup"><span data-stu-id="1023b-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="1023b-105">I comandi aggiunti alla pipeline sono i cmdlet `Get-Process` e `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="1023b-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1023b-106">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="1023b-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="1023b-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1023b-107">See Also</span></span>

[<span data-ttu-id="1023b-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1023b-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
