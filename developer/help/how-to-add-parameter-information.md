---
title: Come aggiungere informazioni sul parametro | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863327"
---
# <a name="how-to-add-parameter-information"></a>Come aggiungere le informazioni sui parametri

Questa sezione descrive come aggiungere il contenuto visualizzato nella sezione dei parametri dell'argomento della Guida del cmdlet. Sezione dei parametri dell'argomento della Guida Elenca ognuno dei parametri del cmdlet e fornisce una descrizione dettagliata di ogni parametro.

Il contenuto della sezione dei parametri deve essere coerenza con il contenuto della sezione relativa alla sintassi dell'argomento della Guida. È responsabilità dell'autore della Guida per assicurarsi che il nodo sia la sintassi e parametri contenga gli elementi XML simile.

> [!NOTE]
> Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell. Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.

### <a name="to-add-parameters"></a>Per aggiungere parametri

1. Aprire il file della Guida e individuare il nodo del comando per il cmdlet che si desidera documentare. Se si aggiunge un nuovo cmdlet che sarà necessario creare un nuovo nodo del comando. Il file della Guida conterrà un nodo del comando per ciascun cmdlet che si stia offrendo contenuto della Guida per. Di seguito è riportato un esempio di un nodo del comando vuoto.

    ```xml
    <command:command>
    </command:command>
    ```

2. All'interno del nodo di comandi, individuare il nodo di descrizione e aggiungere un nodo di parametri, come illustrato di seguito. È consentito un solo nodo parametri e deve seguire immediatamente il nodo della sintassi.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. All'interno del nodo di parametri, aggiungere un nodo di parametro per ogni parametro del cmdlet come illustrato di seguito.

   In questo esempio viene aggiunto un nodo di parametro per i tre parametri.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Poiché questi sono gli stessi tag XML che vengono usati nel nodo di sintassi e perché i parametri specificati di seguito devono corrispondere ai parametri specificati per il nodo della sintassi, è possibile copiare nodi del parametri dal nodo di sintassi e incollarli il nodo parametri. Tuttavia, assicurarsi di copiare solo un'istanza di un nodo di parametro, anche se il parametro è specificato più set di parametri nella sintassi.

4. Per ogni parametro del set di nodi, i valori di attributo che definiscono le caratteristiche di ogni parametro. Questi attributi includono quanto segue: obbligatorio, il glob pipelineinput e posizione.

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

5. Per ogni nodo di parametro, aggiungere il nome del parametro. Di seguito è riportato un esempio del nome del parametro aggiunto al nodo di parametro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Per ogni nodo di parametro, aggiungere la descrizione del parametro. Di seguito è riportato un esempio di descrizione del parametro aggiunto al nodo di parametro.

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

   Di seguito è riportato un esempio del tipo di .NET Framework parametro aggiunto al nodo di parametro.

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

8. Per ogni nodo di parametro, aggiungere il valore predefinito del parametro. La seguente frase viene aggiunto alla descrizione del parametro quando viene visualizzato il contenuto: "DefaultValue" è il valore predefinito.

   Di seguito è riportato un esempio del valore predefinito del parametro viene aggiunto al nodo di parametro.

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

9. Per ogni parametro con valori multipli, aggiungere un nodo di valori possibili.

   Di seguito è riportato un esempio del di un nodo di valori possibili che definisce due valori possibili per il parametro

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

- Gli attributi del parametro non vengono visualizzati in tutte le visualizzazioni dell'argomento della Guida del cmdlet. Tuttavia, questi vengono visualizzati in una tabella seguendo la descrizione del parametro quando l'utente richiede la versione completa (Get-Help \<cmdletname >-completo) o un parametro (Get-Help \<cmdletname >-parametro) visualizzazione dell'argomento.

- Descrizione del parametro è una delle parti più importanti di un argomento della Guida del cmdlet. La descrizione deve essere breve, nonché completa. Inoltre, tenere presente che, se la descrizione del parametro diventa troppo lunga, ad esempio quando due parametri interagiscono tra loro, è possibile aggiungere altri contenuti nella sezione Note dell'argomento della Guida del cmdlet.

  Descrizione del parametro fornisce due tipi di informazioni.

- Ciò che il cmdlet non quando viene usato il parametro.

- Quali un valore valido è per il parametro.

- Poiché i valori dei parametri sono espressi come oggetti .NET Framework, gli utenti devono ulteriori informazioni su questi valori di quanto farebbero in una Guida della riga di comando tradizionali. Stabilire il tipo di dati di parametro è progettato per accettare l'utente e sono inclusi esempi.

Il valore predefinito del parametro è il valore che viene usato se il parametro non è specificato nella riga di comando. Si noti che il valore predefinito è facoltativo e non è necessaria per alcuni parametri, ad esempio parametri obbligatori. Tuttavia, è necessario specificare un valore predefinito per la maggior parte dei parametri facoltativi.

Il valore predefinito consente all'utente di comprendere l'effetto di non usare il parametro. Descrivere il valore predefinito in modo molto specifico, ad esempio la directory"corrente" o "Windows PowerShell directory di installazione ($pshome)" di un percorso facoltativo. È anche possibile scrivere una frase che descrive il valore predefinito, ad esempio la frase seguente usato per il `PassThru` parametro: "Se PassThru viene omesso, il cmdlet non passa gli oggetti nella pipeline."  Inoltre, poiché opposta, il nome del campo viene visualizzato il valore "**il valore predefinito**", non è necessario includere il termine "default value" della voce.

Il valore predefinito del parametro non viene visualizzato in tutte le visualizzazioni dell'argomento della Guida del cmdlet. Tuttavia, viene visualizzato in una tabella (insieme gli attributi di parametro) seguendo la descrizione del parametro quando l'utente richiede la versione completa (Get-Help \<cmdletname >-completo) o un parametro (Get-Help \<cmdletname >-parametro) visualizzazione dell'argomento.

Il codice XML seguente mostra una coppia di `<dev:defaultValue>` tag aggiunti al `<command:parameter>` nodo. Si noti che il valore predefinito seguente subito dopo la chiusura `</command:parameterValue>` tag (quando il valore del parametro è specificato) o la chiusura `</maml:description>` tag della descrizione del parametro. Nome.

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

Aggiungere i valori per i tipi enumerati

Se il parametro ha più valori o valori di un tipo enumerato, è possibile usare facoltativo \<dev:possibleValues > nodo. Questo nodo consente di specificare un nome e una descrizione per specificare più valori.

Tenere presente che le descrizioni dei valori enumerati non sono presenti viste della Guida visualizzate da in uno qualsiasi del valore predefinito di `Get-Help` cmdlet, ma altri visualizzatori Help possono visualizzare questo contenuto nel proprio punto di vista.

Il codice XML seguente viene illustrato un `<dev:possibleValues>` nodo con due valori specificati.

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