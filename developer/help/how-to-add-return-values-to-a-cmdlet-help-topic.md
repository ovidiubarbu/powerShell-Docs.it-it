---
title: Come aggiungere restituiscono valori a un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859437"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Come aggiungere i tipi di valori restituiti a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione OUTPUTS di un argomento della Guida del cmdlet Windows PowerShell®. La sezione di output elenca le classi .NET di oggetti che il cmdlet restituisce o passa alla pipeline.

Non sono previsti limiti al numero di classi che è possibile aggiungere alla sezione degli output. I tipi restituiti di un cmdlet sono racchiusi tra parentesi una \<comando: returnValues > nodo, con ogni classe racchiuso tra parentesi un \<comando: returnValue > elemento.

Se un cmdlet non genera alcun output, usare questa sezione per non indicare che è presente alcun output. Ad esempio, al posto del nome di classe, scrivere "None" e fornire una breve spiegazione. Se il cmdlet genera l'output in modo condizionale, è possibile utilizzare questo nodo vengono presentate le condizioni e descrivere l'output condizionale.

Lo schema include due \<maml:description > elementi in ogni \<comando: returnValue > elemento. Tuttavia, il `Get-Help` cmdlet visualizza soltanto il contenuto del \<returnValue: comando > /\<maml:description > elemento.

A partire da Windows PowerShell 3.0, il `Get-Help` cmdlet consente di visualizzare il contenuto del \<navigationlink > elemento. Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.

Il codice XML seguente viene illustrato il \<maml:returnValues > nodo.

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

Il codice XML seguente viene illustrato un esempio dell'uso di \<maml:returnValues > nodo per documentare un tipo di output.

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



