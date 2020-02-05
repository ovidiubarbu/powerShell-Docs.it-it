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
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995942"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Come aggiungere i tipi di valori restituiti a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione OUTPUTs a un argomento della guida del cmdlet di® di Windows PowerShell. Nella sezione output sono elencate le classi .NET di oggetti restituiti dal cmdlet o che passano dalla pipeline.

Non esiste alcun limite al numero di classi che è possibile aggiungere alla sezione OUTPUTs. I tipi restituiti di un cmdlet sono racchiusi in un comando \<: returnValues > nodo, con ogni classe racchiusa in un \<comando: returnValue > elemento.

Se un cmdlet non genera alcun output, utilizzare questa sezione per indicare che non è presente alcun output. Ad esempio, al posto del nome della classe, scrivere "None" e fornire una breve spiegazione. Se il cmdlet genera l'output in modo condizionale, usare questo nodo per illustrare le condizioni e descrivere l'output condizionale.

Lo schema include due elementi \<maml: Description > in ogni comando \<: returnValue > elemento. Tuttavia, il cmdlet `Get-Help` Visualizza solo il contenuto del comando \<: returnValue >/\<maml: Description > elemento.

A partire da Windows PowerShell 3,0, il cmdlet `Get-Help` Visualizza il contenuto dell'elemento > di \<maml: URI. Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.

Il codice XML seguente mostra il nodo \<maml: returnValues >.

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
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



