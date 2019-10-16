---
title: Come aggiungere valori restituiti a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367800"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Come aggiungere i tipi di valori restituiti a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione OUTPUTs a un argomento della guida del cmdlet di® di Windows PowerShell. Nella sezione output sono elencate le classi .NET di oggetti restituiti dal cmdlet o che passano dalla pipeline.

Non esiste alcun limite al numero di classi che è possibile aggiungere alla sezione OUTPUTs. I tipi restituiti di un cmdlet sono racchiusi in un nodo \<command: returnValues >, in cui ogni classe è racchiusa in un elemento \<command: returnValue >.

Se un cmdlet non genera alcun output, utilizzare questa sezione per indicare che non è presente alcun output. Ad esempio, al posto del nome della classe, scrivere "None" e fornire una breve spiegazione. Se il cmdlet genera l'output in modo condizionale, usare questo nodo per illustrare le condizioni e descrivere l'output condizionale.

Lo schema include due elementi \<maml: Description > in ogni elemento \<command: returnValue >. Tuttavia, il cmdlet `Get-Help` Visualizza solo il contenuto dell'elemento \<command: returnValue >/\<maml: Description >.

A partire da Windows PowerShell 3,0, il cmdlet `Get-Help` Visualizza il contenuto dell'elemento > \<maml: URI. Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.

Nel codice XML seguente viene illustrato il nodo \<maml: returnValues >.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

Nel codice XML seguente viene illustrato un esempio di utilizzo del nodo \<maml: returnValues > per documentare un tipo di output.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



