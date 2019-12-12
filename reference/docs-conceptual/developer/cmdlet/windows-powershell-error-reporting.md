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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364270"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="cb86b-102">Segnalazione di errori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb86b-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="cb86b-103">Negli argomenti di questa sezione viene illustrato il modo in cui i cmdlet segnalano gli errori.</span><span class="sxs-lookup"><span data-stu-id="cb86b-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cb86b-104">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="cb86b-104">In This Section</span></span>

<span data-ttu-id="cb86b-105">[Concetti relativi alla segnalazione degli errori](./error-reporting-concepts.md) Vengono descritti i due meccanismi che i cmdlet possono utilizzare per segnalare gli errori.</span><span class="sxs-lookup"><span data-stu-id="cb86b-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="cb86b-106">[Errori di terminazione](./terminating-errors.md) Descrive il metodo utilizzato per segnalare gli errori di terminazione, in cui il metodo può essere chiamato dall'interno del cmdlet e le eccezioni che possono essere restituite dal runtime di Windows PowerShell quando viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="cb86b-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="cb86b-107">[Errori non fatali](./non-terminating-errors.md) Viene descritto il metodo utilizzato per segnalare errori non fatali e il metodo in cui è possibile chiamare il metodo dall'interno del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb86b-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="cb86b-108">[Visualizzazione delle informazioni sugli errori per categoria](./displaying-error-information.md) Vengono illustrati i modi in cui gli utenti possono visualizzare gli errori.</span><span class="sxs-lookup"><span data-stu-id="cb86b-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="cb86b-109">[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md) Descrive i componenti di un record di errore.</span><span class="sxs-lookup"><span data-stu-id="cb86b-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="cb86b-110">[Interpretazione degli oggetti ErrorRecord](./interpreting-errorrecord-objects.md) Viene illustrato come vengono interpretati gli oggetti ErrorRecord.</span><span class="sxs-lookup"><span data-stu-id="cb86b-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb86b-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cb86b-111">See Also</span></span>

[<span data-ttu-id="cb86b-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb86b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
