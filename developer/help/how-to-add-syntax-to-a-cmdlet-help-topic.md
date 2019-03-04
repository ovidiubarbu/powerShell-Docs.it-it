---
title: Come aggiungere la sintassi per un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 947d0c0188df5bba3a9fb617fe5abf0b3b28eb51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857997"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Come aggiungere la sintassi a un argomento della Guida sui cmdlet

- [Attributi dei parametri](#Parameter-Attributes)

- [Attributi del valore di parametro](#Parameter-Value-Attributes)

- [Informazioni sulla sintassi di raccolta](#Gathering-Syntax-Information)

- [Il diagramma della sintassi XML di codifica](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Aspetti da considerare il diagramma della sintassi nella Guida del Cmdlet

Prima di avviare il codice XML per il diagramma della sintassi nel file della Guida cmdlet del codice, leggere questa sezione per ottenere un quadro preciso del tipo di dati che è necessario specificare, ad esempio gli attributi di parametro e la modalità di visualizzazione che i dati nel diagramma della sintassi...

### <a name="parameter-attributes"></a>Attributi dei parametri

- Obbligatoria

  - Se true, il parametro deve essere presente in tutti i comandi che usano il set di parametri.

  - Se false, il parametro è facoltativo in tutti i comandi che usano il set di parametri.

- Posizione

  - Se un nome, il nome di parametro è obbligatorio.

  - Se è posizionale, il nome del parametro è facoltativo. Quando viene omesso, il valore del parametro deve essere nella posizione specificata nel comando. Ad esempio, se il valore è posizione = "1", il valore del parametro deve essere il primo o l'unico valore di parametro nel comando senza nome.

- Input della pipeline

  - Se true (ByValue), è possibile inviare input tramite pipe al parametro. L'input è associato con ("associazione a") il parametro anche se il nome della proprietà e il tipo di oggetto non corrispondono al tipo previsto. Il comando di Windows PowerShell? i componenti di associazione di parametro tenta di convertire l'input nel tipo corretto e il comando solo quando il tipo non può essere convertito. Per valore, è possibile associare un solo parametro in un set di parametri.

  - Se true (ByPropertyName), è possibile inviare input tramite pipe al parametro. Tuttavia, l'input è associato il parametro solo quando il nome del parametro corrisponde al nome di una proprietà dell'oggetto di input. Ad esempio, se è il nome del parametro `Path`, gli oggetti inviati tramite pipe al cmdlet sono associati a tale parametro solo quando l'oggetto ha una proprietà denominata percorso.

  - Se true (ByValue, ByPropertyName), è possibile inviare input tramite pipe al parametro dal nome della proprietà o dal valore. Per valore, è possibile associare un solo parametro in un set di parametri.

  - Se false, è possibile inviare tramite pipe di input per questo parametro.

- Caratteri jolly

  - Se true, il testo digitato dall'utente per il valore del parametro può includere caratteri jolly.

  - Se false, il testo digitato dall'utente per il valore del parametro non può includere caratteri jolly.

### <a name="parameter-value-attributes"></a>Attributi del valore di parametro

- Obbligatoria

  - Se true, il valore specificato deve essere utilizzato ogni volta che tramite il parametro in un comando.

  - Se false, il valore del parametro è facoltativo. In genere, un valore è facoltativo solo se è uno dei diversi valori validi per un parametro, ad esempio in un tipo enumerato.

L'attributo obbligatorio di un valore di parametro è diverso dall'attributo di un parametro obbligatorio.

L'attributo obbligatorio di un parametro indica se il parametro (e il relativo valore) deve essere inclusi quando si richiama il cmdlet. Al contrario, l'attributo obbligatorio di un valore del parametro viene utilizzato solo quando il parametro è incluso nel comando. Indica se è necessario usare quel valore specifico con il parametro.

In genere, sono necessari i valori dei parametri sono segnaposto e i valori dei parametri sono valori letterali non sono necessari, perché sono uno dei diversi valori che potrebbero essere usati con il parametro.

### <a name="gathering-syntax-information"></a>Informazioni sulla sintassi di raccolta

1. Iniziare con il nome del cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Elencare tutti i parametri del cmdlet. Digitare un trattino (anche noto come "trattino" o "segno" (ASCII 45) prima di ogni nome di parametro. Separare i parametri in set di parametri (alcuni cmdlet potrebbe avere un solo parametro impostato). In questo esempio di Get-Tech cmdlet dispone di due set di parametri.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Avviare ogni parametro impostato con il nome del cmdlet.

   Elencare il set prima di tutto di parametri predefinito. Il parametro predefinito è specificato dalla classe cmdlet.

   Per ogni set di parametri, il parametro univoco primo elenco, a meno che non vi sono parametri posizionali devono trovarsi all'inizio. Nell'esempio precedente, i nome e ID i parametri sono parametri univoci per i due set di parametri (ogni set di parametri deve avere un parametro che è univoco per tale set di parametri). Questo rende più semplice per gli utenti identificare il parametro è necessario fornire per il parametro impostato.

   Elencare i parametri nell'ordine in cui appaiono nel comando. Se l'ordine non è rilevante, elencare i parametri correlati tra loro o elencare innanzitutto i parametri usati più di frequente.

   Assicurarsi di elencare i parametri WhatIf and Confirm se il cmdlet supporta ShouldProcess.

   Non elencano i parametri comuni (ad esempio Verbose, Debug ed ErrorAction) nel diagramma di sintassi. Il `Get-Help` cmdlet aggiunge le informazioni per l'utente quando questo viene visualizzato l'argomento della Guida.

3. Aggiungere i valori dei parametri. In Windows PowerShell?, i valori dei parametri sono rappresentati in base al tipo .NET. Il nome del tipo può tuttavia essere abbreviato, ad esempio "string" per System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abbreviare i tipi, purché il significato è chiaro, ad esempio "string" per System. String e "int" per System.Int32.

   Elencare tutti i valori delle enumerazioni, ad esempio il parametro - type nell'esempio precedente, può essere impostata su "basic" o "avanzata".

   Passare i parametri, ad esempio - elenco dell'esempio precedente, non dispongono di valori.

4. Aggiungere i valori dei parametri che sono segnaposto, rispetto ai valori dei parametri sono valori letterali parentesi angolari.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Racchiudere i parametri facoltativi e i valori mostrati tra parentesi quadre.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Parentesi quadre, racchiudere i nomi dei parametri facoltativi (per i parametri posizionali). Il nome per i parametri posizionali, ad esempio il parametro Name nell'esempio seguente, non è possibile includere nel comando.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Se un valore di parametro può contenere più valori, ad esempio un elenco di nomi nel parametro Name, aggiungere una coppia di parentesi quadre seguono il valore del parametro.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Se l'utente può scegliere tra parametri o valori di parametro, ad esempio il parametro di tipo, racchiudere le scelte tra parentesi graffe e separarle con symbol(;) di OR esclusivo.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Se il valore del parametro deve utilizzare una formattazione specifica, ad esempio virgolette doppie o parentesi tonde, mostrare il formato nella sintassi.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Il diagramma della sintassi XML di codifica

Il nodo di sintassi del XML inizia immediatamente dopo il nodo di description, che termina con il \</maml:description > tag. Per informazioni sulla raccolta dei dati utilizzati nel diagramma della sintassi, vedere [informazioni sulla sintassi di raccolta](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Aggiunta di un nodo di sintassi

Il diagramma della sintassi visualizzato nell'argomento della Guida cmdlet viene generato dai dati nel nodo sintassi del XML. Il nodo della sintassi è racchiuso tra una coppia se \<: sintassi del comando > tag. Con ogni set di parametri del cmdlet racchiuso tra una coppia di \<comando: syntaxitem > tag. Non sono previsti limiti al numero di \<comando: syntaxitem > tag che è possibile aggiungere.

L'esempio seguente illustra un nodo di sintassi che dispone di nodi di elemento di sintassi per due set di parametri.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Aggiunta del nome del Cmdlet al parametro del Set di dati

Ogni set di parametri del cmdlet è specificato in un nodo di elemento di sintassi. Ogni nodo di elemento di sintassi inizia con una coppia di \<maml:name > tag che includono il nome del cmdlet.

L'esempio seguente include un nodo di sintassi che dispone di nodi di elemento di sintassi per due set di parametri.

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

Ogni parametro aggiunto al nodo di elemento di sintassi viene specificato all'interno di una coppia di \<: parametro del comando > tag. Necessaria una coppia di \<: parametro del comando > tag per ogni parametro incluso nel set di parametri, fatta eccezione per i parametri comuni fornite da Windows PowerShell.

Gli attributi dell'apertura \<: parametro del comando > tag determinano il modo in cui il parametro viene visualizzato nel diagramma della sintassi. Per informazioni sugli attributi di parametro, vedere [attributi di parametro](#Parameter-Attributes).

> [!NOTE]
> Il \<: parametro del comando > tag supporta un elemento figlio \<maml:description > il cui contenuto non viene mai visualizzato. Le descrizioni dei parametri vengono specificati nel nodo parametro del codice XML. Per evitare le incoerenze tra le informazioni nell'elemento di sintassi bodes e il nodo di parametro, omettere il (\<maml:description > o lasciarlo vuoto.

L'esempio seguente include un nodo di elemento di sintassi per un set con due parametri di parametri.

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
