---
title: Segnalazione errori di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067094"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="39725-102">Segnalazione di errori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="39725-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="39725-103">Gli argomenti in questa sezione descrivono come i cmdlet di segnalano gli errori.</span><span class="sxs-lookup"><span data-stu-id="39725-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="39725-104">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="39725-104">In This Section</span></span>

<span data-ttu-id="39725-105">[Concetti relativi a Reporting errore](./error-reporting-concepts.md) descrive i due meccanismi che i cmdlet è possono usare per segnalare gli errori.</span><span class="sxs-lookup"><span data-stu-id="39725-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="39725-106">[Irreversibili](./terminating-errors.md) descrive il metodo utilizzato per segnalare terminazione errori, in cui tale metodo può essere chiamato dall'interno il cmdlet sia le eccezioni che possono essere restituite dal runtime di Windows PowerShell quando viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="39725-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="39725-107">[Gli errori non irreversibili](./non-terminating-errors.md) descrive il metodo utilizzato per segnalare gli errori non fatali e in cui tale metodo può essere chiamato dall'interno il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39725-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="39725-108">[Visualizzazione di informazioni sugli errori per categoria](./displaying-error-information.md) illustra i modi che gli utenti possono visualizzare l'errore.</span><span class="sxs-lookup"><span data-stu-id="39725-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="39725-109">[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md) descrive i componenti di un record di errore.</span><span class="sxs-lookup"><span data-stu-id="39725-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="39725-110">[L'interpretazione di oggetti ErrorRecord](./interpreting-errorrecord-objects.md) viene illustrato come vengono interpretati ErrorRecord oggetti.</span><span class="sxs-lookup"><span data-stu-id="39725-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="39725-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39725-111">See Also</span></span>

[<span data-ttu-id="39725-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="39725-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
