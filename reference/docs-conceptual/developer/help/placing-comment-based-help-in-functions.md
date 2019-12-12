---
title: Inserimento della Guida basata su commenti in funzioni | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367780"
---
# <a name="placing-comment-based-help-in-functions"></a>Inserimento della Guida basata sui commenti nelle funzioni

In questo argomento viene illustrato dove posizionare la guida basata su commenti per una funzione in modo che il cmdlet `Get-Help` associ l'argomento della guida basato sui commenti con la funzione corretta.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Posizione della Guida basata su commenti per una funzione

- All'inizio del corpo della funzione.

- Alla fine del corpo della funzione.

- Prima della parola chiave `Function`. Quando la funzione si trova in uno script o in un modulo di script, non può essere presente più di una riga vuota tra l'ultima riga della Guida basata su commenti e la parola chiave `Function`. In caso contrario, `Get-Help` associa la Guida allo script, non alla funzione.

## <a name="examples-of-help-placement-in-a-function"></a>Esempi di posizionamento della Guida in una funzione

 Gli esempi seguenti illustrano ognuna delle tre opzioni di selezione host per la guida basata su commenti per una funzione.

### <a name="help-at-the-beginning-of-a-function-body"></a>Guida all'inizio del corpo di una funzione

 Nell'esempio seguente viene illustrato l'oggetto basato su commenti all'inizio del corpo di una funzione.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Guida alla fine del corpo di una funzione

 Nell'esempio seguente viene illustrato un oggetto basato su commenti alla fine del corpo di una funzione.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Guida prima della parola chiave Function

 Negli esempi seguenti viene illustrato il commento basato sulla riga prima della parola chiave Function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```