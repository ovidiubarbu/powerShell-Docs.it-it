---
title: L'inserimento della Guida basata sui commenti nelle funzioni | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857947"
---
# <a name="placing-comment-based-help-in-functions"></a>Inserimento della Guida basata sui commenti nelle funzioni

Questo argomento viene illustrato dove posizionare la Guida basata su commenti per una funzione in modo che il `Get-Help` cmdlet consente di associare l'argomento della Guida basata sui commenti con la funzione corretta.

## <a name="where-to-place-comment-based-help-for-a-function"></a>La posizione della Guida basata su commenti per una funzione

- All'inizio del corpo della funzione.

- Alla fine del corpo della funzione.

- Prima di `Function` (parola chiave). Quando la funzione è in uno script o un modulo di script, non può esistere più di una riga vuota tra l'ultima riga delle informazioni della Guida basata sui commenti e i `Function` (parola chiave). In caso contrario, `Get-Help` associa la Guida in linea con lo script, non con la funzione.

## <a name="examples-of-help-placement-in-a-function"></a>Esempi di posizionamento della Guida in una funzione

 Gli esempi seguenti illustrano le opzioni di selezione host per tre della Guida basata su commenti per una funzione.

### <a name="help-at-the-beginning-of-a-function-body"></a>Guida in linea all'inizio di un corpo di funzione

 Nell'esempio seguente viene basata sui commenti all'inizio di un corpo della funzione.

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

### <a name="help-at-the-end-of-a-function-body"></a>Guida alla fine di un corpo di funzione

 Nell'esempio seguente viene basata sui commenti alla fine di un corpo della funzione.

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

### <a name="help-before-the-function-keyword"></a>Guida in linea prima della parola chiave (funzione)

 Gli esempi seguenti mostrano basata sui commenti sulla riga prima della parola chiave di funzione.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```