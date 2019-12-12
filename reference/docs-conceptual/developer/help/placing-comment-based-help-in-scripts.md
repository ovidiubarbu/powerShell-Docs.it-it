---
title: Inserimento della Guida basata su commenti negli script | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361180"
---
# <a name="placing-comment-based-help-in-scripts"></a>Inserimento della Guida basata sui commenti negli script

In questo argomento viene illustrato dove posizionare la guida basata su commenti per uno script in modo che il cmdlet `Get-Help` associ l'argomento della guida basato sui commenti con gli script e non con le funzioni eventualmente presenti nello script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Posizione della Guida basata su commenti per uno script

- All'inizio del file di script. La guida per gli script può essere preceduta dallo script solo da commenti e righe vuote.

- Alla fine del file di script.

  Se il primo elemento nel corpo dello script (dopo la guida) è una dichiarazione di funzione, devono essere presenti almeno due righe vuote tra la fine della Guida per lo script e la dichiarazione di funzione. In caso contrario, la guida viene interpretata come la guida per la funzione, non per la guida per lo script.

## <a name="examples-of-help-placement-in-a-script"></a>Esempi di posizionamento della Guida in uno script

 Negli esempi seguenti vengono illustrate tutte le opzioni di selezione host per la guida basata su commenti per uno script.

### <a name="help-at-the-beginning-of-a-script"></a>Guida all'inizio di uno script

 Nell'esempio seguente viene illustrato come basato su commenti all'inizio di uno script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Guida alla fine di uno script

 Nell'esempio seguente viene illustrato come basato su commenti alla fine di uno script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```