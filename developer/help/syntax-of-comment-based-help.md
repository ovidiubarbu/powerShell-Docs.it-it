---
title: Sintassi della Guida basata sui commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855547"
---
# <a name="syntax-of-comment-based-help"></a>Sintassi della Guida basata sui commenti

In questa sezione viene descritta la sintassi della Guida basata sui commenti.

## <a name="syntax-diagram"></a>Diagramma della sintassi

 La sintassi per la Guida basata sui commenti è come segue:

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

 La Guida basata sui commenti viene scritto come una serie di commenti. È possibile digitare un simbolo di commento (#) prima di ogni riga dei commenti, oppure è possibile usare la "\<&" e "& >" simboli per creare un blocco di commento. Tutte le righe all'interno del blocco di commento vengono interpretate come commenti.

 Ogni sezione della Guida basata sui commenti è definito da una parola chiave e ogni parola chiave è preceduto da un punto (.). Le parole chiave possono essere visualizzati in qualsiasi ordine. I nomi di parola chiave non sono tra maiuscole e minuscole.

 Un blocco di commento deve contenere almeno una parola chiave della Guida. Alcune delle parole chiave, come esempio, possono apparire più volte nello stesso blocco di commento. Il contenuto della Guida per ogni parola chiave inizia la riga dopo la parola chiave e può estendersi su più righe.

 Tutte le righe in un argomento della Guida basata sui commenti devono essere contigue. Se un argomento della Guida basata sui commenti segue un commento che non fa parte dell'argomento della Guida, deve esistere almeno una riga vuota tra l'ultima riga di commento non-Help e l'inizio degli argomenti della Guida basata sui commenti.

 Ad esempio, contiene il seguente argomento della Guida basata sui commenti di. Parola chiave di descrizione e il relativo valore, che è una descrizione di una funzione o script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```