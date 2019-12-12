---
title: Come aggiungere esempi a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368110"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Come aggiungere esempi a un argomento della Guida sui cmdlet

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Informazioni sugli esempi nella Guida dei cmdlet

- Elencare tutti i nomi di parametro nel comando, anche quando i nomi dei parametri sono facoltativi. Questo consente all'utente di interpretare il comando con facilità.

- Evitare gli alias e i nomi di parametro parziali, anche se funzionano in® di Windows PowerShell.

- Nella descrizione dell'esempio, spiegare il razionale per la costruzione del comando. Spiegare il motivo per cui si sono scelti parametri e valori specifici e come usare le variabili.

- Se il comando usa espressioni, spiegarle in dettaglio.

- Se il comando USA proprietà e metodi di oggetti, in particolare le proprietà che non vengono visualizzate nella visualizzazione predefinita, usare l'esempio come opportunità per informare l'utente sull'oggetto.

## <a name="help-views-that-display-examples"></a>Viste della guida che visualizzano esempi

Gli esempi vengono visualizzati solo nella visualizzazione dettagliata e completa della guida del cmdlet.

## <a name="adding-an-examples-node"></a>Aggiunta di un nodo esempi

Nel codice XML seguente viene illustrato come aggiungere un nodo esempi contenente un singolo nodo di esempio. Aggiungere altri nodi di esempio per ogni esempio che si desidera includere nell'argomento.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Aggiunta di un titolo di esempio

Nel codice XML seguente viene illustrato come aggiungere un titolo per l'esempio. Il titolo viene usato per impostare l'esempio oltre ad altri esempi. Windows PowerShell® usa un'intestazione standard che include un numero di esempio sequenziale.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Aggiunta di caratteri precedenti

Nel codice XML seguente viene illustrato come aggiungere caratteri, ad esempio il prompt di Windows PowerShell, che vengono visualizzati immediatamente prima del comando di esempio (senza spazi intermedi). Windows PowerShell® usa il prompt di Windows PowerShell: C:\PS >.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Aggiunta del comando

Nel codice XML seguente viene illustrato come aggiungere il comando effettivo dell'esempio. Quando si aggiunge il comando, digitare l'intero nome (non usare alias) di cmdlet e parametri. Inoltre, quando possibile, utilizzare caratteri minuscoli.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Aggiunta di una descrizione

Nel codice XML seguente viene illustrato come aggiungere una descrizione per l'esempio. Windows PowerShell® usa un singolo set di tag \<maml: para > per la descrizione, anche se è possibile usare più tag \<maml: para >.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Aggiunta dell'output di esempio

Nel codice XML seguente viene illustrato come aggiungere l'output del comando. Le informazioni sui risultati del comando sono facoltative, ma in alcuni casi è utile illustrare l'effetto dell'utilizzo di parametri specifici. Windows PowerShell® usa due set di tag blank \<maml: para > per separare l'output del comando dal comando.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```