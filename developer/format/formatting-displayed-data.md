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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065666"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="5b474-102">Formattazione dei dati visualizzati</span><span class="sxs-lookup"><span data-stu-id="5b474-102">Formatting Displayed Data</span></span>

<span data-ttu-id="5b474-103">È possibile specificare la modalità di visualizzazione singoli punti dati dell'elenco, una tabella o una visualizzazione più ampia.</span><span class="sxs-lookup"><span data-stu-id="5b474-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="5b474-104">È possibile usare la `FormatString` elemento quando si definiscono gli elementi di visualizzazione, oppure è possibile usare il `ScriptBlock` elemento per chiamare il `FormatString` metodo sui dati.</span><span class="sxs-lookup"><span data-stu-id="5b474-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="5b474-105">Usando l'elemento FormatString</span><span class="sxs-lookup"><span data-stu-id="5b474-105">Using the FormatString Element</span></span>

<span data-ttu-id="5b474-106">Nell'esempio seguente il valore della `TotalProcessorTime` proprietà del [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetto viene formattato usando l'elemento FormatString.</span><span class="sxs-lookup"><span data-stu-id="5b474-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="5b474-107">Il `TotalProcessorTime` proprietà</span><span class="sxs-lookup"><span data-stu-id="5b474-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



