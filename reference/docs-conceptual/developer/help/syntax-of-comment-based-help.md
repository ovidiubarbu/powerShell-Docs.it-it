---
title: Sintassi della Guida basata su Commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367760"
---
# <a name="syntax-of-comment-based-help"></a>Sintassi della Guida basata sui commenti

In questa sezione viene descritta la sintassi della Guida basata su commenti.

## <a name="syntax-diagram"></a>Diagramma della sintassi

 La sintassi per la guida basata su commenti è la seguente:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Descrizione della sintassi

 La guida basata su commenti viene scritta come una serie di commenti. È possibile digitare un simbolo di commento (#) prima di ogni riga di commenti oppure è possibile usare i simboli "\< #" e "# >" per creare un blocco di commento. Tutte le righe all'interno del blocco di commento vengono interpretate come commenti.

 Ogni sezione della Guida basata su commenti è definita da una parola chiave e ogni parola chiave è preceduta da un punto (.). Le parole chiave possono essere visualizzate in qualsiasi ordine. I nomi delle parole chiave non fanno distinzione tra maiuscole e minuscole.

 Un blocco di commento deve contenere almeno una parola chiave della guida. Alcune parole chiave, ad esempio, possono essere visualizzate più volte nello stesso blocco di commento. Il contenuto della Guida per ogni parola chiave inizia sulla riga dopo la parola chiave e può estendersi su più righe.

 Tutte le righe in un argomento della Guida basata su commenti devono essere contigue. Se un argomento della guida basato su commenti segue un commento che non fa parte dell'argomento della guida, deve essere presente almeno una riga vuota tra l'ultima riga di commento non della guida e l'inizio della Guida basata su commenti.

 Ad esempio, l'argomento della guida basato su Commenti seguente contiene. Parola chiave Description e relativo valore, che è una descrizione di una funzione o di uno script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```