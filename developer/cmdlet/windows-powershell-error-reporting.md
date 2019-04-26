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
# <a name="windows-powershell-error-reporting"></a>Segnalazione di errori di Windows PowerShell

Gli argomenti in questa sezione descrivono come i cmdlet di segnalano gli errori.

## <a name="in-this-section"></a>Contenuto della sezione

[Concetti relativi a Reporting errore](./error-reporting-concepts.md) descrive i due meccanismi che i cmdlet è possono usare per segnalare gli errori.

[Irreversibili](./terminating-errors.md) descrive il metodo utilizzato per segnalare terminazione errori, in cui tale metodo può essere chiamato dall'interno il cmdlet sia le eccezioni che possono essere restituite dal runtime di Windows PowerShell quando viene chiamato il metodo.

[Gli errori non irreversibili](./non-terminating-errors.md) descrive il metodo utilizzato per segnalare gli errori non fatali e in cui tale metodo può essere chiamato dall'interno il cmdlet.

[Visualizzazione di informazioni sugli errori per categoria](./displaying-error-information.md) illustra i modi che gli utenti possono visualizzare l'errore.

[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md) descrive i componenti di un record di errore.

[L'interpretazione di oggetti ErrorRecord](./interpreting-errorrecord-objects.md) viene illustrato come vengono interpretati ErrorRecord oggetti.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
