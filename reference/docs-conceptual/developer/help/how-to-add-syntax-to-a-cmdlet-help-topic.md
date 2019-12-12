---
title: Come aggiungere la sintassi a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361210"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Come aggiungere la sintassi a un argomento della Guida sui cmdlet

Prima di iniziare a scrivere il codice XML per il diagramma della sintassi nel file della guida del cmdlet, leggere questa sezione per ottenere un quadro chiaro del tipo di dati che è necessario fornire, ad esempio gli attributi dei parametri, e la modalità di visualizzazione dei dati nel diagramma della sintassi.

### <a name="parameter-attributes"></a>Attributi dei parametri

- Obbligatoria

  - Se true, il parametro deve essere visualizzato in tutti i comandi che usano il set di parametri.

  - Se false, il parametro è facoltativo in tutti i comandi che usano il set di parametri.

- Posizione

  - Se denominato, il nome del parametro è obbligatorio.

  - Se posizionale, il nome del parametro è facoltativo. Quando viene omesso, il valore del parametro deve trovarsi nella posizione specificata nel comando. Se, ad esempio, il valore è position = "1", il valore del parametro deve essere il primo o l'unico valore di parametro senza nome nel comando.

- Input pipeline

  - Se true (ByValue), è possibile inviare input tramite pipe al parametro. L'input è associato al parametro ("associato a") anche se il nome della proprietà e il tipo di oggetto non corrispondono al tipo previsto. Windows PowerShell? i componenti di associazione dei parametri tentano di convertire l'input nel tipo corretto e non riescono a eseguire il comando solo quando non è possibile convertire il tipo. È possibile associare un solo parametro in un set di parametri in base al valore.

  - Se true (ByPropertyName), è possibile inviare input tramite pipe al parametro. Tuttavia, l'input è associato al parametro solo quando il nome del parametro corrisponde al nome di una proprietà dell'oggetto di input. Se, ad esempio, il nome del parametro è `Path`, gli oggetti inviati tramite pipe al cmdlet sono associati a tale parametro solo quando l'oggetto dispone di una proprietà denominata Path.

  - Se true (ByValue, ByPropertyName), è possibile inviare input tramite pipe al parametro in base al nome della proprietà o al valore. È possibile associare un solo parametro in un set di parametri in base al valore.

  - Se false, non è possibile inviare input tramite pipe a questo parametro.

- Glob

  - Se true, il testo che l'utente digita per il valore del parametro può includere caratteri jolly.

  - Se false, il testo che l'utente digita per il valore del parametro non può includere caratteri jolly.

### <a name="parameter-value-attributes"></a>Attributi valore parametro

- Obbligatoria

  - Se true, il valore specificato deve essere utilizzato quando si utilizza il parametro in un comando.

  - Se false, il valore del parametro è facoltativo. In genere, un valore è facoltativo solo quando è uno dei diversi valori validi per un parametro, ad esempio in un tipo enumerato.

L'attributo obbligatorio di un valore di parametro è diverso dall'attributo obbligatorio di un parametro.

L'attributo obbligatorio di un parametro indica se il parametro (e il relativo valore) deve essere incluso quando si richiama il cmdlet. Al contrario, l'attributo obbligatorio di un valore di parametro viene utilizzato solo quando il parametro viene incluso nel comando. Indica se il valore specifico deve essere utilizzato con il parametro.

In genere, i valori dei parametri che sono segnaposto sono obbligatori e i valori di parametro letterali non sono obbligatori, perché sono uno dei diversi valori che potrebbero essere utilizzati con il parametro.

### <a name="gathering-syntax-information"></a>Raccolta di informazioni sulla sintassi

1. Iniziare con il nome del cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Elencare tutti i parametri del cmdlet. Digitare un trattino (noto anche come "Dash" o "segno meno" (ASCII 45) prima di ogni nome di parametro. Separare i parametri in set di parametri (alcuni cmdlet possono avere un solo set di parametri). In questo esempio il cmdlet Get-Tech dispone di due set di parametri.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Avviare ogni set di parametri con il nome del cmdlet.

   Elencare prima il set di parametri predefinito. Il parametro predefinito viene specificato dalla classe cmdlet.

   Per ogni set di parametri, elencare prima il parametro univoco, a meno che non siano presenti parametri posizionali che devono essere visualizzati per primi. Nell'esempio precedente, i parametri Name e ID sono parametri univoci per i due set di parametri (ogni set di parametri deve avere un parametro univoco per quel set di parametri). Questo rende più semplice per gli utenti identificare il parametro che è necessario fornire per il set di parametri.

   Elencare i parametri nell'ordine in cui devono essere visualizzati nel comando. Se l'ordine non è rilevante, elencare insieme i parametri correlati oppure elencare prima i parametri usati più di frequente.

   Assicurarsi di elencare i parametri WhatIf e Confirm se il cmdlet supporta ShouldProcess.

   Non elencare i parametri comuni, ad esempio Verbose, debug e ErrorAction, nel diagramma della sintassi. Il cmdlet `Get-Help` aggiunge tali informazioni quando Visualizza l'argomento della guida.

3. Aggiungere i valori dei parametri. In Windows PowerShell, i valori dei parametri sono rappresentati dal tipo .NET. Il nome del tipo, tuttavia, può essere abbreviato, ad esempio "String" per System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abbreviare i tipi a condizione che il significato sia chiaro, ad esempio "String" per System. String e "int" per System. Int32.

   Elencare tutti i valori delle enumerazioni, ad esempio il parametro-Type nell'esempio precedente, che può essere impostato su "Basic" o "Advanced".

   I parametri switch, ad esempio-List nell'esempio precedente, non dispongono di valori.

4. Aggiungere le parentesi angolari ai valori dei parametri segnaposto, rispetto ai valori di parametro letterali.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Racchiudere i parametri facoltativi e i relativi valori tra parentesi quadre.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Racchiudere i nomi dei parametri facoltativi (per i parametri posizionali) tra parentesi quadre. Il nome dei parametri posizionali, ad esempio il parametro Name nell'esempio seguente, non deve essere incluso nel comando.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Se un valore di parametro può contenere più valori, ad esempio un elenco di nomi nel parametro Name, aggiungere una coppia di parentesi quadre direttamente dopo il valore del parametro.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Se l'utente può scegliere tra parametri o valori di parametro, ad esempio il parametro di tipo, racchiudere le scelte tra parentesi graffe e separarle con il simbolo OR esclusivo (;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Se il valore del parametro deve usare una formattazione specifica, ad esempio virgolette o parentesi, Mostra il formato nella sintassi.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Codifica del diagramma di sintassi XML

Il nodo della sintassi del codice XML inizia subito dopo il nodo Description, che termina con il tag \</maml: Description >. Per informazioni sulla raccolta dei dati utilizzati nel diagramma della sintassi, vedere [raccolta di informazioni sulla sintassi](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Aggiunta di un nodo della sintassi

Il diagramma della sintassi visualizzato nell'argomento della guida del cmdlet viene generato dai dati nel nodo Syntax del codice XML. Il nodo della sintassi è racchiuso in una coppia se \<comando: Syntax > Tags. Con ogni set di parametri del cmdlet racchiuso in una coppia di \<comando: syntaxitem > Tag. Non esiste alcun limite al numero di \<comando: syntaxitem > Tag che è possibile aggiungere.

Nell'esempio seguente viene illustrato un nodo della sintassi con nodi di elementi della sintassi per due set di parametri.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Aggiunta del nome del cmdlet ai dati del set di parametri

Ogni set di parametri del cmdlet viene specificato in un nodo elemento della sintassi. Ogni nodo dell'elemento della sintassi inizia con una coppia di \<maml: Name > Tag che includono il nome del cmdlet.

Nell'esempio seguente viene incluso un nodo della sintassi con nodi di elementi della sintassi per due set di parametri.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Aggiunta di parametri

Ogni parametro aggiunto al nodo elemento sintassi viene specificato in una coppia di \<comando: parametro > Tag. È necessario disporre di una coppia di \<comando: parametro > Tag per ogni parametro incluso nel set di parametri, ad eccezione dei parametri comuni forniti da Windows PowerShell?.

Gli attributi del comando di \<di apertura: parametro > Tag determinano il modo in cui il parametro viene visualizzato nel diagramma della sintassi. Per informazioni sugli attributi dei parametri, vedere [attributi dei parametri](#parameter-attributes).

> [!NOTE]
> Il \<comando: parametro > Tag supporta un elemento figlio \<maml: Description > il cui contenuto non viene mai visualizzato. Le descrizioni dei parametri sono specificate nel nodo Parameter del codice XML. Per evitare incoerenze tra le informazioni nell'elemento di sintassi Bodes e il nodo del parametro, omettere il (\<maml: Description > o lasciarlo vuoto.

Nell'esempio seguente viene incluso un nodo elemento della sintassi per un set di parametri con due parametri.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
