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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363700"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="dcd8a-102">Formattazione dei dati visualizzati</span><span class="sxs-lookup"><span data-stu-id="dcd8a-102">Formatting Displayed Data</span></span>

<span data-ttu-id="dcd8a-103">È possibile specificare la modalità di visualizzazione dei singoli punti dati nell'elenco, nella tabella o nella visualizzazione estesa.</span><span class="sxs-lookup"><span data-stu-id="dcd8a-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="dcd8a-104">È possibile utilizzare l'elemento `FormatString` quando si definiscono gli elementi della visualizzazione oppure è possibile utilizzare l'elemento `ScriptBlock` per chiamare il metodo `FormatString` sui dati.</span><span class="sxs-lookup"><span data-stu-id="dcd8a-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="dcd8a-105">Utilizzo dell'elemento FormatString</span><span class="sxs-lookup"><span data-stu-id="dcd8a-105">Using the FormatString Element</span></span>

<span data-ttu-id="dcd8a-106">Nell'esempio seguente il valore della proprietà `TotalProcessorTime` dell'oggetto [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) viene formattato usando l'elemento FormatString.</span><span class="sxs-lookup"><span data-stu-id="dcd8a-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="dcd8a-107">Proprietà `TotalProcessorTime`</span><span class="sxs-lookup"><span data-stu-id="dcd8a-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



