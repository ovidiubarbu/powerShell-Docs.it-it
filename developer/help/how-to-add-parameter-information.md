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
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="7c13d-102">Come aggiungere le informazioni sui parametri</span><span class="sxs-lookup"><span data-stu-id="7c13d-102">How to Add Parameter Information</span></span>

<span data-ttu-id="7c13d-103">Questa sezione descrive come aggiungere il contenuto visualizzato nella sezione dei parametri dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c13d-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c13d-104">Sezione dei parametri dell'argomento della Guida Elenca ognuno dei parametri del cmdlet e fornisce una descrizione dettagliata di ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="7c13d-105">Il contenuto della sezione dei parametri deve essere coerenza con il contenuto della sezione relativa alla sintassi dell'argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="7c13d-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="7c13d-106">È responsabilità dell'autore della Guida per assicurarsi che il nodo sia la sintassi e parametri contenga gli elementi XML simile.</span><span class="sxs-lookup"><span data-stu-id="7c13d-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="7c13d-107">Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c13d-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="7c13d-108">Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c13d-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="7c13d-109">Per aggiungere parametri</span><span class="sxs-lookup"><span data-stu-id="7c13d-109">To Add Parameters</span></span>

1. <span data-ttu-id="7c13d-110">Aprire il file della Guida e individuare il nodo del comando per il cmdlet che si desidera documentare.</span><span class="sxs-lookup"><span data-stu-id="7c13d-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="7c13d-111">Se si aggiunge un nuovo cmdlet che sarà necessario creare un nuovo nodo del comando.</span><span class="sxs-lookup"><span data-stu-id="7c13d-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="7c13d-112">Il file della Guida conterrà un nodo del comando per ciascun cmdlet che si stia offrendo contenuto della Guida per.</span><span class="sxs-lookup"><span data-stu-id="7c13d-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="7c13d-113">Di seguito è riportato un esempio di un nodo del comando vuoto.</span><span class="sxs-lookup"><span data-stu-id="7c13d-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="7c13d-114">All'interno del nodo di comandi, individuare il nodo di descrizione e aggiungere un nodo di parametri, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="7c13d-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="7c13d-115">È consentito un solo nodo parametri e deve seguire immediatamente il nodo della sintassi.</span><span class="sxs-lookup"><span data-stu-id="7c13d-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="7c13d-116">All'interno del nodo di parametri, aggiungere un nodo di parametro per ogni parametro del cmdlet come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="7c13d-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="7c13d-117">In questo esempio viene aggiunto un nodo di parametro per i tre parametri.</span><span class="sxs-lookup"><span data-stu-id="7c13d-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="7c13d-118">Poiché questi sono gli stessi tag XML che vengono usati nel nodo di sintassi e perché i parametri specificati di seguito devono corrispondere ai parametri specificati per il nodo della sintassi, è possibile copiare nodi del parametri dal nodo di sintassi e incollarli il nodo parametri.</span><span class="sxs-lookup"><span data-stu-id="7c13d-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="7c13d-119">Tuttavia, assicurarsi di copiare solo un'istanza di un nodo di parametro, anche se il parametro è specificato più set di parametri nella sintassi.</span><span class="sxs-lookup"><span data-stu-id="7c13d-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="7c13d-120">Per ogni parametro del set di nodi, i valori di attributo che definiscono le caratteristiche di ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="7c13d-121">Questi attributi includono quanto segue: obbligatorio, il glob pipelineinput e posizione.</span><span class="sxs-lookup"><span data-stu-id="7c13d-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="7c13d-122">Per ogni nodo di parametro, aggiungere il nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="7c13d-123">Di seguito è riportato un esempio del nome del parametro aggiunto al nodo di parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="7c13d-124">Per ogni nodo di parametro, aggiungere la descrizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="7c13d-125">Di seguito è riportato un esempio di descrizione del parametro aggiunto al nodo di parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="7c13d-126">Per ogni nodo di parametro, aggiungere il tipo di .NET Framework del parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="7c13d-127">Il tipo di parametro viene visualizzato insieme al nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="7c13d-128">Di seguito è riportato un esempio del tipo di .NET Framework parametro aggiunto al nodo di parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="7c13d-129">Per ogni nodo di parametro, aggiungere il valore predefinito del parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="7c13d-130">La seguente frase viene aggiunto alla descrizione del parametro quando viene visualizzato il contenuto: "DefaultValue" è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="7c13d-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="7c13d-131">Di seguito è riportato un esempio del valore predefinito del parametro viene aggiunto al nodo di parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="7c13d-132">Per ogni parametro con valori multipli, aggiungere un nodo di valori possibili.</span><span class="sxs-lookup"><span data-stu-id="7c13d-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="7c13d-133">Di seguito è riportato un esempio del di un nodo di valori possibili che definisce due valori possibili per il parametro</span><span class="sxs-lookup"><span data-stu-id="7c13d-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="7c13d-134">Ecco alcuni aspetti da ricordare quando si aggiungono parametri.</span><span class="sxs-lookup"><span data-stu-id="7c13d-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="7c13d-135">Gli attributi del parametro non vengono visualizzati in tutte le visualizzazioni dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c13d-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="7c13d-136">Tuttavia, questi vengono visualizzati in una tabella seguendo la descrizione del parametro quando l'utente richiede la versione completa (Get-Help \<cmdletname >-completo) o un parametro (Get-Help \<cmdletname >-parametro) visualizzazione dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="7c13d-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="7c13d-137">Descrizione del parametro è una delle parti più importanti di un argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c13d-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="7c13d-138">La descrizione deve essere breve, nonché completa.</span><span class="sxs-lookup"><span data-stu-id="7c13d-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="7c13d-139">Inoltre, tenere presente che, se la descrizione del parametro diventa troppo lunga, ad esempio quando due parametri interagiscono tra loro, è possibile aggiungere altri contenuti nella sezione Note dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c13d-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="7c13d-140">Descrizione del parametro fornisce due tipi di informazioni.</span><span class="sxs-lookup"><span data-stu-id="7c13d-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="7c13d-141">Ciò che il cmdlet non quando viene usato il parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="7c13d-142">Quali un valore valido è per il parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="7c13d-143">Poiché i valori dei parametri sono espressi come oggetti .NET Framework, gli utenti devono ulteriori informazioni su questi valori di quanto farebbero in una Guida della riga di comando tradizionali.</span><span class="sxs-lookup"><span data-stu-id="7c13d-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="7c13d-144">Stabilire il tipo di dati di parametro è progettato per accettare l'utente e sono inclusi esempi.</span><span class="sxs-lookup"><span data-stu-id="7c13d-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="7c13d-145">Il valore predefinito del parametro è il valore che viene usato se il parametro non è specificato nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="7c13d-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="7c13d-146">Si noti che il valore predefinito è facoltativo e non è necessaria per alcuni parametri, ad esempio parametri obbligatori.</span><span class="sxs-lookup"><span data-stu-id="7c13d-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="7c13d-147">Tuttavia, è necessario specificare un valore predefinito per la maggior parte dei parametri facoltativi.</span><span class="sxs-lookup"><span data-stu-id="7c13d-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="7c13d-148">Il valore predefinito consente all'utente di comprendere l'effetto di non usare il parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="7c13d-149">Descrivere il valore predefinito in modo molto specifico, ad esempio la directory"corrente" o "Windows PowerShell directory di installazione ($pshome)" di un percorso facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7c13d-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="7c13d-150">È anche possibile scrivere una frase che descrive il valore predefinito, ad esempio la frase seguente usato per il `PassThru` parametro: "Se PassThru viene omesso, il cmdlet non passa gli oggetti nella pipeline."</span><span class="sxs-lookup"><span data-stu-id="7c13d-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="7c13d-151">Inoltre, poiché opposta, il nome del campo viene visualizzato il valore "**il valore predefinito**", non è necessario includere il termine "default value" della voce.</span><span class="sxs-lookup"><span data-stu-id="7c13d-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="7c13d-152">Il valore predefinito del parametro non viene visualizzato in tutte le visualizzazioni dell'argomento della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c13d-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="7c13d-153">Tuttavia, viene visualizzato in una tabella (insieme gli attributi di parametro) seguendo la descrizione del parametro quando l'utente richiede la versione completa (Get-Help \<cmdletname >-completo) o un parametro (Get-Help \<cmdletname >-parametro) visualizzazione dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="7c13d-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="7c13d-154">Il codice XML seguente mostra una coppia di `<dev:defaultValue>` tag aggiunti al `<command:parameter>` nodo.</span><span class="sxs-lookup"><span data-stu-id="7c13d-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="7c13d-155">Si noti che il valore predefinito seguente subito dopo la chiusura `</command:parameterValue>` tag (quando il valore del parametro è specificato) o la chiusura `</maml:description>` tag della descrizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="7c13d-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="7c13d-156">Nome.</span><span class="sxs-lookup"><span data-stu-id="7c13d-156">name.</span></span>

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

<span data-ttu-id="7c13d-157">Aggiungere i valori per i tipi enumerati</span><span class="sxs-lookup"><span data-stu-id="7c13d-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="7c13d-158">Se il parametro ha più valori o valori di un tipo enumerato, è possibile usare facoltativo \<dev:possibleValues > nodo.</span><span class="sxs-lookup"><span data-stu-id="7c13d-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="7c13d-159">Questo nodo consente di specificare un nome e una descrizione per specificare più valori.</span><span class="sxs-lookup"><span data-stu-id="7c13d-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="7c13d-160">Tenere presente che le descrizioni dei valori enumerati non sono presenti viste della Guida visualizzate da in uno qualsiasi del valore predefinito di `Get-Help` cmdlet, ma altri visualizzatori Help possono visualizzare questo contenuto nel proprio punto di vista.</span><span class="sxs-lookup"><span data-stu-id="7c13d-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="7c13d-161">Il codice XML seguente viene illustrato un `<dev:possibleValues>` nodo con due valori specificati.</span><span class="sxs-lookup"><span data-stu-id="7c13d-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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