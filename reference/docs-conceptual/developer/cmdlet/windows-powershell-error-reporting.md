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
# <a name="windows-powershell-error-reporting"></a>Segnalazione di errori di Windows PowerShell

Negli argomenti di questa sezione viene illustrato il modo in cui i cmdlet segnalano gli errori.

## <a name="in-this-section"></a>Contenuto della sezione

[Concetti relativi alla segnalazione degli errori](./error-reporting-concepts.md) Vengono descritti i due meccanismi che i cmdlet possono utilizzare per segnalare gli errori.

[Errori di terminazione](./terminating-errors.md) Descrive il metodo utilizzato per segnalare gli errori di terminazione, in cui il metodo può essere chiamato dall'interno del cmdlet e le eccezioni che possono essere restituite dal runtime di Windows PowerShell quando viene chiamato il metodo.

[Errori non fatali](./non-terminating-errors.md) Viene descritto il metodo utilizzato per segnalare errori non fatali e il metodo in cui è possibile chiamare il metodo dall'interno del cmdlet.

[Visualizzazione delle informazioni sugli errori per categoria](./displaying-error-information.md) Vengono illustrati i modi in cui gli utenti possono visualizzare gli errori.

[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md) Descrive i componenti di un record di errore.

[Interpretazione degli oggetti ErrorRecord](./interpreting-errorrecord-objects.md) Viene illustrato come vengono interpretati gli oggetti ErrorRecord.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
