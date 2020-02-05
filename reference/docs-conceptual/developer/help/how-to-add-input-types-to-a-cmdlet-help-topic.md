---
title: Come aggiungere tipi di input a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: 37af16d0279b6487c78f90eb19bcfe5c152ed9e7
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996048"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Come aggiungere i tipi di input a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione INPUTs a un argomento della Guida di Windows PowerShell® cmdlet. La sezione INPUTs elenca le classi .NET di oggetti accettati dal cmdlet come input dalla pipeline, in base al valore o al nome della proprietà.

Non esiste alcun limite al numero di classi che è possibile aggiungere a una sezione di input. I tipi di input sono racchiusi in un \<comando: inputTypes > nodo, con ogni classe racchiusa in un \<comando: inputType > elemento.

Lo schema include due elementi \<maml: Description > in ogni \<comando: inputType > elemento. Tuttavia, il cmdlet `Get-Help` Visualizza solo il contenuto dell'elemento \<Command: inputType >/\<maml: Description >).

A partire da Windows PowerShell 3,0, il cmdlet `Get-Help` Visualizza il contenuto dell'elemento > di \<maml: URI. Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.

Il codice XML seguente mostra il nodo di > \<maml: inputTypes.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Nel codice XML seguente viene illustrato un esempio di utilizzo del nodo \<maml: inputTypes > per documentare un tipo di input.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```