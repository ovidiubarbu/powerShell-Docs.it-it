---
title: Come aggiungere esempi per un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857317"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Come aggiungere esempi a un argomento della Guida sui cmdlet

- [Informazioni importanti informazioni sugli esempi nella Guida del Cmdlet](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [Viste della Guida che consentono di visualizzare esempi](#Help-Views-that-Display-Examples)

- [Aggiunta di un nodo di esempi](#Adding-an-Examples-Node)

- [Aggiunta di caratteri che lo precedono](#Adding-Preceding-Characters)

- [Aggiunta del comando](#Adding-the-Command)

- [Aggiunta di una descrizione](#Adding-a-Description)

- [Aggiunta dell'Output di esempio](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Informazioni importanti informazioni sugli esempi nella Guida del Cmdlet

- Elencare tutti i nomi dei parametri nel comando, anche quando i nomi dei parametri sono facoltativi. Ciò consente all'utente di interpretare il comando con facilità.

- Evitare gli alias e i nomi di parametri parziale, anche se funzionano in Windows PowerShell®.

- Nella descrizione dell'esempio, spiegare il motivo per la costruzione del comando. Spiegare il motivo per cui si è scelto di determinati parametri e valori e utilizzo di variabili.

- Se il comando Usa le espressioni, li descrivono in dettaglio.

- Se il comando Usa le proprietà e metodi di oggetti, in particolare le proprietà che non vengono visualizzati nella visualizzazione predefinita, usare l'esempio come un'opportunità informare l'utente sull'oggetto.

## <a name="help-views-that-display-examples"></a>Viste della Guida che consentono di visualizzare esempi

Negli esempi vengono visualizzati solo in viste dettagliata e completa della Guida dei cmdlet.

## <a name="adding-an-examples-node"></a>Aggiunta di un nodo di esempi

Il codice XML seguente viene illustrato come aggiungere un nodo di esempi contenente un singolo nodo di esempio. Aggiungere nodi di esempio aggiuntive per ogni esempi da includere nell'argomento.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Aggiunta di un titolo di esempio

Il codice XML seguente viene illustrato come aggiungere un titolo per l'esempio. Il titolo utilizzato per impostare l'esempio a parte di altri esempi. Windows PowerShell® Usa un'intestazione standard che include un numero sequenziale di esempio.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Aggiunta di caratteri che lo precedono

Il codice XML seguente viene illustrato come aggiungere caratteri, ad esempio i prompt di Windows PowerShell, che vengono visualizzati immediatamente prima del comando di esempio (senza spazi intermedi). Windows PowerShell® Usa il prompt dei comandi di Windows PowerShell: C:\PS&GT; &GT;.

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

Il codice XML seguente viene illustrato come aggiungere il comando effettivo dell'esempio. Quando si aggiunge il comando, digitare il nome completo (non usare alias) dei cmdlet e parametri. Inoltre, usare caratteri minuscoli quando possibile.

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

Il codice XML seguente viene illustrato come aggiungere una descrizione per l'esempio. Windows PowerShell® Usa un singolo set di \<maml: para > tag per la descrizione, anche se più \<maml: para > tag possono essere usati.

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

## <a name="adding-example-output"></a>Aggiunta dell'Output di esempio

Il codice XML seguente viene illustrato come aggiungere l'output del comando. Le informazioni relative ai risultati del comando sono facoltativi, ma in alcuni casi è utile illustrare l'effetto dell'uso di parametri specifici. Windows PowerShell® usa due set di spazio vuoto \<maml: para > tag per separare l'output del comando del comando.

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