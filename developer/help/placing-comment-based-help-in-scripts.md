---
title: L'inserimento della Guida basata sui commenti negli script | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083230"
---
# <a name="placing-comment-based-help-in-scripts"></a>Inserimento della Guida basata sui commenti negli script

Questo argomento viene illustrato dove posizionare la Guida basata su commenti per uno script in modo che il `Get-Help` cmdlet consente di associare l'argomento della Guida basata sui commenti con gli script e non con le funzioni che potrebbero essere nello script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>La posizione della Guida basata su commenti per uno Script

- All'inizio del file di script. Lo script Help può essere preceduto nello script solo per i commenti e le righe vuote.

- Alla fine del file di script.

  Se il primo elemento nel corpo dello script (dopo la Guida in linea) è una dichiarazione di funzione, deve esserci almeno due righe vuote tra la fine dello script della Guida in linea e la dichiarazione di funzione. In caso contrario, la Guida in linea viene interpretato come guida per la funzione, non della Guida per lo script.

## <a name="examples-of-help-placement-in-a-script"></a>Esempi di posizionamento della Guida in uno Script

 Gli esempi seguenti illustrano le opzioni di posizionamento della Guida basata su commenti per uno script.

### <a name="help-at-the-beginning-of-a-script"></a>Guida in linea all'inizio di uno Script

 Nell'esempio seguente viene basata sui commenti all'inizio di uno script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Guida alla fine di uno Script

 Nell'esempio seguente viene basata sui commenti alla fine di uno script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```