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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363700"
---
# <a name="formatting-displayed-data"></a>Formattazione dei dati visualizzati

È possibile specificare la modalità di visualizzazione dei singoli punti dati nell'elenco, nella tabella o nella visualizzazione estesa. È possibile utilizzare l'elemento `FormatString` quando si definiscono gli elementi della visualizzazione oppure è possibile utilizzare l'elemento `ScriptBlock` per chiamare il metodo `FormatString` sui dati.

## <a name="using-the-formatstring-element"></a>Utilizzo dell'elemento FormatString

Nell'esempio seguente il valore della proprietà `TotalProcessorTime` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) viene formattato usando l'elemento FormatString. Proprietà `TotalProcessorTime`

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



