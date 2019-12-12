---
title: Come aggiungere informazioni sui parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361230"
---
# <a name="how-to-add-parameter-information"></a>Come aggiungere le informazioni sui parametri

In questa sezione viene descritto come aggiungere contenuto che viene visualizzato nella sezione dei parametri dell'argomento della guida del cmdlet. Nella sezione PARAMETERS dell'argomento della guida vengono elencati tutti i parametri del cmdlet e viene fornita una descrizione dettagliata di ogni parametro.

Il contenuto della sezione PARAMETERS deve essere coerente con il contenuto della sezione relativa alla sintassi dell'argomento della guida. È responsabilità dell'autore della Guida assicurarsi che il nodo sintassi e parametri contenga elementi XML simili.

> [!NOTE]
> Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell. Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.

### <a name="to-add-parameters"></a>Per aggiungere parametri

1. Aprire il file della guida del cmdlet e individuare il nodo di comando per il cmdlet che si sta documentando. Se si aggiunge un nuovo cmdlet, sarà necessario creare un nuovo nodo di comando. Il file della Guida conterrà un nodo di comando per ogni cmdlet per il quale si fornisce contenuto della guida. Di seguito è riportato un esempio di un nodo di comando vuoto.

    ```xml
    <command:command>
    </command:command>
    ```

2. All'interno del nodo Command individuare il nodo Description e aggiungere un nodo Parameters, come illustrato di seguito. È consentito un solo nodo Parameters, che deve seguire immediatamente il nodo Syntax.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Nel nodo parametri aggiungere un nodo parametro per ogni parametro del cmdlet, come illustrato di seguito.

   In questo esempio viene aggiunto un nodo parametro per tre parametri.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Poiché si tratta degli stessi tag XML utilizzati nel nodo della sintassi e perché i parametri specificati qui devono corrispondere ai parametri specificati dal nodo della sintassi, è possibile copiare i nodi del parametro dal nodo della sintassi e incollarli nel nodo parametri. Tuttavia, assicurarsi di copiare solo un'istanza di un nodo di parametro, anche se il parametro è specificato in più set di parametri nella sintassi.

4. Per ogni nodo di parametro, impostare i valori di attributo che definiscono le caratteristiche di ogni parametro. Sono inclusi i seguenti attributi: required, Glob, PipelineInput e position.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Per ogni nodo di parametro, aggiungere il nome del parametro. Di seguito è riportato un esempio del nome del parametro aggiunto al nodo del parametro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Per ogni nodo di parametro, aggiungere la descrizione del parametro. Di seguito è riportato un esempio della descrizione del parametro aggiunta al nodo del parametro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Per ogni nodo di parametro, aggiungere il tipo di .NET Framework del parametro. Il tipo di parametro viene visualizzato insieme al nome del parametro.

   Di seguito è riportato un esempio del parametro .NET Framework tipo aggiunto al nodo del parametro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Per ogni nodo di parametro, aggiungere il valore predefinito del parametro. Quando viene visualizzato il contenuto, alla descrizione del parametro viene aggiunta la frase seguente: "DefaultValue" è il valore predefinito.

   Di seguito è riportato un esempio del valore predefinito del parametro aggiunto al nodo del parametro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Per ogni parametro con più valori, aggiungere un nodo valori possibili.

   Di seguito è riportato un esempio di un nodo valori possibili che definisce due valori possibili per il parametro

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Ecco alcuni aspetti da ricordare quando si aggiungono parametri.

- Gli attributi del parametro non vengono visualizzati in tutte le visualizzazioni dell'argomento della guida del cmdlet. Tuttavia, vengono visualizzati in una tabella che segue la descrizione del parametro quando l'utente chiede la vista completa (Get-Help \<CmdletName >-Full) o Parameter (Get-Help \<CmdletName >-Parameter) dell'argomento.

- La descrizione del parametro è una delle parti più importanti di un argomento della guida del cmdlet. La descrizione deve essere breve, nonché approfondita. Tenere inoltre presente che se la descrizione del parametro diventa troppo lungo, ad esempio quando due parametri interagiscono tra loro, è possibile aggiungere altro contenuto nella sezione Note dell'argomento della guida del cmdlet.

  La descrizione del parametro fornisce due tipi di informazioni.

- Operazioni svolte dal cmdlet quando viene utilizzato il parametro.

- Qual è un valore valido per il parametro.

- Poiché i valori dei parametri sono espressi come .NET Framework oggetti, per gli utenti sono necessarie altre informazioni su questi valori rispetto a una guida tradizionale della riga di comando. Indicare all'utente il tipo di dati che il parametro è progettato per accettare e includere esempi.

Il valore predefinito del parametro è il valore utilizzato se il parametro non è specificato nella riga di comando. Si noti che il valore predefinito è facoltativo e non è necessario per alcuni parametri, ad esempio i parametri obbligatori. Tuttavia, è necessario specificare un valore predefinito per la maggior parte dei parametri facoltativi.

Il valore predefinito consente all'utente di comprendere l'effetto di non utilizzare il parametro. Descrivere il valore predefinito in modo specifico, ad esempio "directory corrente" o "directory di installazione di Windows PowerShell ($pshome)" per un percorso facoltativo. È anche possibile scrivere una frase che descrive il valore predefinito, ad esempio la frase seguente usata per il parametro `PassThru`: "se PassThru non è specificato, il cmdlet non passa gli oggetti alla pipeline."  Inoltre, poiché il valore viene visualizzato in senso opposto al nome del campo "**valore predefinito**", non è necessario includere il termine "valore predefinito" nella voce.

Il valore predefinito del parametro non viene visualizzato in tutte le visualizzazioni dell'argomento della guida del cmdlet. Viene tuttavia visualizzato in una tabella, insieme agli attributi dei parametri, dopo la descrizione del parametro quando l'utente chiede la visualizzazione completa (Get-Help \<CmdletName >-Full) o Parameter (Get-Help \<CmdletName >-Parameter) dell'argomento.

Nel codice XML seguente viene illustrata una coppia di tag `<dev:defaultValue>` aggiunti al nodo `<command:parameter>`. Si noti che il valore predefinito segue immediatamente dopo il tag di chiusura `</command:parameterValue>` (quando viene specificato il valore del parametro) o il tag di chiusura `</maml:description>` della descrizione del parametro. name.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Aggiungere valori per i tipi enumerati

Se il parametro ha più valori o valori di un tipo enumerato, è possibile usare un nodo facoltativo \<dev: possibleValues >. Questo nodo consente di specificare un nome e una descrizione per più valori.

Tenere presente che le descrizioni dei valori enumerati non vengono visualizzate in nessuna delle visualizzazioni della guida predefinite visualizzate dal cmdlet `Get-Help`, ma gli altri visualizzatori della guida possono visualizzare questo contenuto nelle visualizzazioni.

Nel codice XML seguente viene illustrato un nodo `<dev:possibleValues>` con due valori specificati.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```