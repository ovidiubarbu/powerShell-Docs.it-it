---
title: Come aggiungere i tipi di Input a un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860807"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Come aggiungere i tipi di input a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere una sezione input a un argomento della Guida del cmdlet Windows PowerShell®. La sezione input sono elencate le classi .NET di oggetti che il cmdlet accetta come input dalla pipeline, in base al valore o al nome di proprietà.

Non sono previsti limiti al numero di classi che è possibile aggiungere a una sezione input. I tipi di input sono racchiusi in un \<comando: inputTypes > nodo, con ogni classe racchiuso tra parentesi un \<comando: inputType > elemento.

Lo schema include due \<maml:description > elementi in ogni \<comando: inputType > elemento. Tuttavia, il `Get-Help` cmdlet visualizza soltanto il contenuto del \<inputType: comando > /\<maml:description >) elemento.

A partire da Windows PowerShell 3.0, il `Get-Help` cmdlet consente di visualizzare il contenuto del \<navigationlink > elemento. Questo elemento consente di indirizzare gli utenti ad argomenti che descrivono la classe .NET.

Il codice XML seguente viene illustrato il \<maml:inputTypes > nodo.

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

Il codice XML seguente viene illustrato un esempio dell'uso di \<maml:inputTypes > nodo per documentare un tipo di input.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```