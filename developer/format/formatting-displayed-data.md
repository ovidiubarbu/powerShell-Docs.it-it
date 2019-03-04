---
title: Formattazione dei dati visualizzati | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854987"
---
# <a name="formatting-displayed-data"></a>Formattazione dei dati visualizzati

È possibile specificare la modalità di visualizzazione singoli punti dati dell'elenco, una tabella o una visualizzazione più ampia. È possibile usare la `FormatString` elemento quando si definiscono gli elementi di visualizzazione, oppure è possibile usare il `ScriptBlock` elemento per chiamare il `FormatString` metodo sui dati.

## <a name="using-the-formatstring-element"></a>Usando l'elemento FormatString

Nell'esempio seguente il valore della `TotalProcessorTime` proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto viene formattato usando l'elemento FormatString. Il `TotalProcessorTime` proprietà

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



