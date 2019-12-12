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
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="1019c-102">Come aggiungere le informazioni sui parametri</span><span class="sxs-lookup"><span data-stu-id="1019c-102">How to Add Parameter Information</span></span>

<span data-ttu-id="1019c-103">In questa sezione viene descritto come aggiungere contenuto che viene visualizzato nella sezione dei parametri dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1019c-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="1019c-104">Nella sezione PARAMETERS dell'argomento della guida vengono elencati tutti i parametri del cmdlet e viene fornita una descrizione dettagliata di ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="1019c-105">Il contenuto della sezione PARAMETERS deve essere coerente con il contenuto della sezione relativa alla sintassi dell'argomento della guida.</span><span class="sxs-lookup"><span data-stu-id="1019c-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="1019c-106">È responsabilità dell'autore della Guida assicurarsi che il nodo sintassi e parametri contenga elementi XML simili.</span><span class="sxs-lookup"><span data-stu-id="1019c-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="1019c-107">Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1019c-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="1019c-108">Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1019c-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="1019c-109">Per aggiungere parametri</span><span class="sxs-lookup"><span data-stu-id="1019c-109">To Add Parameters</span></span>

1. <span data-ttu-id="1019c-110">Aprire il file della guida del cmdlet e individuare il nodo di comando per il cmdlet che si sta documentando.</span><span class="sxs-lookup"><span data-stu-id="1019c-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="1019c-111">Se si aggiunge un nuovo cmdlet, sarà necessario creare un nuovo nodo di comando.</span><span class="sxs-lookup"><span data-stu-id="1019c-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="1019c-112">Il file della Guida conterrà un nodo di comando per ogni cmdlet per il quale si fornisce contenuto della guida.</span><span class="sxs-lookup"><span data-stu-id="1019c-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="1019c-113">Di seguito è riportato un esempio di un nodo di comando vuoto.</span><span class="sxs-lookup"><span data-stu-id="1019c-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="1019c-114">All'interno del nodo Command individuare il nodo Description e aggiungere un nodo Parameters, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="1019c-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="1019c-115">È consentito un solo nodo Parameters, che deve seguire immediatamente il nodo Syntax.</span><span class="sxs-lookup"><span data-stu-id="1019c-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="1019c-116">Nel nodo parametri aggiungere un nodo parametro per ogni parametro del cmdlet, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="1019c-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="1019c-117">In questo esempio viene aggiunto un nodo parametro per tre parametri.</span><span class="sxs-lookup"><span data-stu-id="1019c-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="1019c-118">Poiché si tratta degli stessi tag XML utilizzati nel nodo della sintassi e perché i parametri specificati qui devono corrispondere ai parametri specificati dal nodo della sintassi, è possibile copiare i nodi del parametro dal nodo della sintassi e incollarli nel nodo parametri.</span><span class="sxs-lookup"><span data-stu-id="1019c-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="1019c-119">Tuttavia, assicurarsi di copiare solo un'istanza di un nodo di parametro, anche se il parametro è specificato in più set di parametri nella sintassi.</span><span class="sxs-lookup"><span data-stu-id="1019c-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="1019c-120">Per ogni nodo di parametro, impostare i valori di attributo che definiscono le caratteristiche di ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="1019c-121">Sono inclusi i seguenti attributi: required, Glob, PipelineInput e position.</span><span class="sxs-lookup"><span data-stu-id="1019c-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="1019c-122">Per ogni nodo di parametro, aggiungere il nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="1019c-123">Di seguito è riportato un esempio del nome del parametro aggiunto al nodo del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="1019c-124">Per ogni nodo di parametro, aggiungere la descrizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="1019c-125">Di seguito è riportato un esempio della descrizione del parametro aggiunta al nodo del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="1019c-126">Per ogni nodo di parametro, aggiungere il tipo di .NET Framework del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="1019c-127">Il tipo di parametro viene visualizzato insieme al nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="1019c-128">Di seguito è riportato un esempio del parametro .NET Framework tipo aggiunto al nodo del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="1019c-129">Per ogni nodo di parametro, aggiungere il valore predefinito del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="1019c-130">Quando viene visualizzato il contenuto, alla descrizione del parametro viene aggiunta la frase seguente: "DefaultValue" è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="1019c-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="1019c-131">Di seguito è riportato un esempio del valore predefinito del parametro aggiunto al nodo del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="1019c-132">Per ogni parametro con più valori, aggiungere un nodo valori possibili.</span><span class="sxs-lookup"><span data-stu-id="1019c-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="1019c-133">Di seguito è riportato un esempio di un nodo valori possibili che definisce due valori possibili per il parametro</span><span class="sxs-lookup"><span data-stu-id="1019c-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="1019c-134">Ecco alcuni aspetti da ricordare quando si aggiungono parametri.</span><span class="sxs-lookup"><span data-stu-id="1019c-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="1019c-135">Gli attributi del parametro non vengono visualizzati in tutte le visualizzazioni dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1019c-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="1019c-136">Tuttavia, vengono visualizzati in una tabella che segue la descrizione del parametro quando l'utente chiede la vista completa (Get-Help \<CmdletName >-Full) o Parameter (Get-Help \<CmdletName >-Parameter) dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="1019c-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="1019c-137">La descrizione del parametro è una delle parti più importanti di un argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1019c-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="1019c-138">La descrizione deve essere breve, nonché approfondita.</span><span class="sxs-lookup"><span data-stu-id="1019c-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="1019c-139">Tenere inoltre presente che se la descrizione del parametro diventa troppo lungo, ad esempio quando due parametri interagiscono tra loro, è possibile aggiungere altro contenuto nella sezione Note dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1019c-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="1019c-140">La descrizione del parametro fornisce due tipi di informazioni.</span><span class="sxs-lookup"><span data-stu-id="1019c-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="1019c-141">Operazioni svolte dal cmdlet quando viene utilizzato il parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="1019c-142">Qual è un valore valido per il parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="1019c-143">Poiché i valori dei parametri sono espressi come .NET Framework oggetti, per gli utenti sono necessarie altre informazioni su questi valori rispetto a una guida tradizionale della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="1019c-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="1019c-144">Indicare all'utente il tipo di dati che il parametro è progettato per accettare e includere esempi.</span><span class="sxs-lookup"><span data-stu-id="1019c-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="1019c-145">Il valore predefinito del parametro è il valore utilizzato se il parametro non è specificato nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="1019c-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="1019c-146">Si noti che il valore predefinito è facoltativo e non è necessario per alcuni parametri, ad esempio i parametri obbligatori.</span><span class="sxs-lookup"><span data-stu-id="1019c-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="1019c-147">Tuttavia, è necessario specificare un valore predefinito per la maggior parte dei parametri facoltativi.</span><span class="sxs-lookup"><span data-stu-id="1019c-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="1019c-148">Il valore predefinito consente all'utente di comprendere l'effetto di non utilizzare il parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="1019c-149">Descrivere il valore predefinito in modo specifico, ad esempio "directory corrente" o "directory di installazione di Windows PowerShell ($pshome)" per un percorso facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1019c-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="1019c-150">È anche possibile scrivere una frase che descrive il valore predefinito, ad esempio la frase seguente usata per il parametro `PassThru`: "se PassThru non è specificato, il cmdlet non passa gli oggetti alla pipeline."</span><span class="sxs-lookup"><span data-stu-id="1019c-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="1019c-151">Inoltre, poiché il valore viene visualizzato in senso opposto al nome del campo "**valore predefinito**", non è necessario includere il termine "valore predefinito" nella voce.</span><span class="sxs-lookup"><span data-stu-id="1019c-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="1019c-152">Il valore predefinito del parametro non viene visualizzato in tutte le visualizzazioni dell'argomento della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1019c-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="1019c-153">Viene tuttavia visualizzato in una tabella, insieme agli attributi dei parametri, dopo la descrizione del parametro quando l'utente chiede la visualizzazione completa (Get-Help \<CmdletName >-Full) o Parameter (Get-Help \<CmdletName >-Parameter) dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="1019c-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="1019c-154">Nel codice XML seguente viene illustrata una coppia di tag `<dev:defaultValue>` aggiunti al nodo `<command:parameter>`.</span><span class="sxs-lookup"><span data-stu-id="1019c-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="1019c-155">Si noti che il valore predefinito segue immediatamente dopo il tag di chiusura `</command:parameterValue>` (quando viene specificato il valore del parametro) o il tag di chiusura `</maml:description>` della descrizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="1019c-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="1019c-156">name.</span><span class="sxs-lookup"><span data-stu-id="1019c-156">name.</span></span>

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

<span data-ttu-id="1019c-157">Aggiungere valori per i tipi enumerati</span><span class="sxs-lookup"><span data-stu-id="1019c-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="1019c-158">Se il parametro ha più valori o valori di un tipo enumerato, è possibile usare un nodo facoltativo \<dev: possibleValues >.</span><span class="sxs-lookup"><span data-stu-id="1019c-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="1019c-159">Questo nodo consente di specificare un nome e una descrizione per più valori.</span><span class="sxs-lookup"><span data-stu-id="1019c-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="1019c-160">Tenere presente che le descrizioni dei valori enumerati non vengono visualizzate in nessuna delle visualizzazioni della guida predefinite visualizzate dal cmdlet `Get-Help`, ma gli altri visualizzatori della guida possono visualizzare questo contenuto nelle visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="1019c-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="1019c-161">Nel codice XML seguente viene illustrato un nodo `<dev:possibleValues>` con due valori specificati.</span><span class="sxs-lookup"><span data-stu-id="1019c-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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