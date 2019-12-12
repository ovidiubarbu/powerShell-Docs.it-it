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
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="bbb70-102">Come aggiungere la sintassi a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="bbb70-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="bbb70-103">Prima di iniziare a scrivere il codice XML per il diagramma della sintassi nel file della guida del cmdlet, leggere questa sezione per ottenere un quadro chiaro del tipo di dati che è necessario fornire, ad esempio gli attributi dei parametri, e la modalità di visualizzazione dei dati nel diagramma della sintassi.</span><span class="sxs-lookup"><span data-stu-id="bbb70-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="bbb70-104">Attributi dei parametri</span><span class="sxs-lookup"><span data-stu-id="bbb70-104">Parameter Attributes</span></span>

- <span data-ttu-id="bbb70-105">Obbligatoria</span><span class="sxs-lookup"><span data-stu-id="bbb70-105">Required</span></span>

  - <span data-ttu-id="bbb70-106">Se true, il parametro deve essere visualizzato in tutti i comandi che usano il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="bbb70-107">Se false, il parametro è facoltativo in tutti i comandi che usano il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="bbb70-108">Posizione</span><span class="sxs-lookup"><span data-stu-id="bbb70-108">Position</span></span>

  - <span data-ttu-id="bbb70-109">Se denominato, il nome del parametro è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="bbb70-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="bbb70-110">Se posizionale, il nome del parametro è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bbb70-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="bbb70-111">Quando viene omesso, il valore del parametro deve trovarsi nella posizione specificata nel comando.</span><span class="sxs-lookup"><span data-stu-id="bbb70-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="bbb70-112">Se, ad esempio, il valore è position = "1", il valore del parametro deve essere il primo o l'unico valore di parametro senza nome nel comando.</span><span class="sxs-lookup"><span data-stu-id="bbb70-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="bbb70-113">Input pipeline</span><span class="sxs-lookup"><span data-stu-id="bbb70-113">Pipeline Input</span></span>

  - <span data-ttu-id="bbb70-114">Se true (ByValue), è possibile inviare input tramite pipe al parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="bbb70-115">L'input è associato al parametro ("associato a") anche se il nome della proprietà e il tipo di oggetto non corrispondono al tipo previsto.</span><span class="sxs-lookup"><span data-stu-id="bbb70-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="bbb70-116">Windows PowerShell? i componenti di associazione dei parametri tentano di convertire l'input nel tipo corretto e non riescono a eseguire il comando solo quando non è possibile convertire il tipo.</span><span class="sxs-lookup"><span data-stu-id="bbb70-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="bbb70-117">È possibile associare un solo parametro in un set di parametri in base al valore.</span><span class="sxs-lookup"><span data-stu-id="bbb70-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="bbb70-118">Se true (ByPropertyName), è possibile inviare input tramite pipe al parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="bbb70-119">Tuttavia, l'input è associato al parametro solo quando il nome del parametro corrisponde al nome di una proprietà dell'oggetto di input.</span><span class="sxs-lookup"><span data-stu-id="bbb70-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="bbb70-120">Se, ad esempio, il nome del parametro è `Path`, gli oggetti inviati tramite pipe al cmdlet sono associati a tale parametro solo quando l'oggetto dispone di una proprietà denominata Path.</span><span class="sxs-lookup"><span data-stu-id="bbb70-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="bbb70-121">Se true (ByValue, ByPropertyName), è possibile inviare input tramite pipe al parametro in base al nome della proprietà o al valore.</span><span class="sxs-lookup"><span data-stu-id="bbb70-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="bbb70-122">È possibile associare un solo parametro in un set di parametri in base al valore.</span><span class="sxs-lookup"><span data-stu-id="bbb70-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="bbb70-123">Se false, non è possibile inviare input tramite pipe a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="bbb70-124">Glob</span><span class="sxs-lookup"><span data-stu-id="bbb70-124">Globbing</span></span>

  - <span data-ttu-id="bbb70-125">Se true, il testo che l'utente digita per il valore del parametro può includere caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="bbb70-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="bbb70-126">Se false, il testo che l'utente digita per il valore del parametro non può includere caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="bbb70-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="bbb70-127">Attributi valore parametro</span><span class="sxs-lookup"><span data-stu-id="bbb70-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="bbb70-128">Obbligatoria</span><span class="sxs-lookup"><span data-stu-id="bbb70-128">Required</span></span>

  - <span data-ttu-id="bbb70-129">Se true, il valore specificato deve essere utilizzato quando si utilizza il parametro in un comando.</span><span class="sxs-lookup"><span data-stu-id="bbb70-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="bbb70-130">Se false, il valore del parametro è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="bbb70-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="bbb70-131">In genere, un valore è facoltativo solo quando è uno dei diversi valori validi per un parametro, ad esempio in un tipo enumerato.</span><span class="sxs-lookup"><span data-stu-id="bbb70-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="bbb70-132">L'attributo obbligatorio di un valore di parametro è diverso dall'attributo obbligatorio di un parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="bbb70-133">L'attributo obbligatorio di un parametro indica se il parametro (e il relativo valore) deve essere incluso quando si richiama il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbb70-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="bbb70-134">Al contrario, l'attributo obbligatorio di un valore di parametro viene utilizzato solo quando il parametro viene incluso nel comando.</span><span class="sxs-lookup"><span data-stu-id="bbb70-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="bbb70-135">Indica se il valore specifico deve essere utilizzato con il parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="bbb70-136">In genere, i valori dei parametri che sono segnaposto sono obbligatori e i valori di parametro letterali non sono obbligatori, perché sono uno dei diversi valori che potrebbero essere utilizzati con il parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="bbb70-137">Raccolta di informazioni sulla sintassi</span><span class="sxs-lookup"><span data-stu-id="bbb70-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="bbb70-138">Iniziare con il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbb70-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="bbb70-139">Elencare tutti i parametri del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbb70-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="bbb70-140">Digitare un trattino (noto anche come "Dash" o "segno meno" (ASCII 45) prima di ogni nome di parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="bbb70-141">Separare i parametri in set di parametri (alcuni cmdlet possono avere un solo set di parametri).</span><span class="sxs-lookup"><span data-stu-id="bbb70-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="bbb70-142">In questo esempio il cmdlet Get-Tech dispone di due set di parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="bbb70-143">Avviare ogni set di parametri con il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbb70-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="bbb70-144">Elencare prima il set di parametri predefinito.</span><span class="sxs-lookup"><span data-stu-id="bbb70-144">List the default parameter set first.</span></span> <span data-ttu-id="bbb70-145">Il parametro predefinito viene specificato dalla classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbb70-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="bbb70-146">Per ogni set di parametri, elencare prima il parametro univoco, a meno che non siano presenti parametri posizionali che devono essere visualizzati per primi.</span><span class="sxs-lookup"><span data-stu-id="bbb70-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="bbb70-147">Nell'esempio precedente, i parametri Name e ID sono parametri univoci per i due set di parametri (ogni set di parametri deve avere un parametro univoco per quel set di parametri).</span><span class="sxs-lookup"><span data-stu-id="bbb70-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="bbb70-148">Questo rende più semplice per gli utenti identificare il parametro che è necessario fornire per il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="bbb70-149">Elencare i parametri nell'ordine in cui devono essere visualizzati nel comando.</span><span class="sxs-lookup"><span data-stu-id="bbb70-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="bbb70-150">Se l'ordine non è rilevante, elencare insieme i parametri correlati oppure elencare prima i parametri usati più di frequente.</span><span class="sxs-lookup"><span data-stu-id="bbb70-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="bbb70-151">Assicurarsi di elencare i parametri WhatIf e Confirm se il cmdlet supporta ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="bbb70-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="bbb70-152">Non elencare i parametri comuni, ad esempio Verbose, debug e ErrorAction, nel diagramma della sintassi.</span><span class="sxs-lookup"><span data-stu-id="bbb70-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="bbb70-153">Il cmdlet `Get-Help` aggiunge tali informazioni quando Visualizza l'argomento della guida.</span><span class="sxs-lookup"><span data-stu-id="bbb70-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="bbb70-154">Aggiungere i valori dei parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-154">Add the parameter values.</span></span> <span data-ttu-id="bbb70-155">In Windows PowerShell, i valori dei parametri sono rappresentati dal tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="bbb70-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="bbb70-156">Il nome del tipo, tuttavia, può essere abbreviato, ad esempio "String" per System. String.</span><span class="sxs-lookup"><span data-stu-id="bbb70-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="bbb70-157">Abbreviare i tipi a condizione che il significato sia chiaro, ad esempio "String" per System. String e "int" per System. Int32.</span><span class="sxs-lookup"><span data-stu-id="bbb70-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="bbb70-158">Elencare tutti i valori delle enumerazioni, ad esempio il parametro-Type nell'esempio precedente, che può essere impostato su "Basic" o "Advanced".</span><span class="sxs-lookup"><span data-stu-id="bbb70-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="bbb70-159">I parametri switch, ad esempio-List nell'esempio precedente, non dispongono di valori.</span><span class="sxs-lookup"><span data-stu-id="bbb70-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="bbb70-160">Aggiungere le parentesi angolari ai valori dei parametri segnaposto, rispetto ai valori di parametro letterali.</span><span class="sxs-lookup"><span data-stu-id="bbb70-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="bbb70-161">Racchiudere i parametri facoltativi e i relativi valori tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="bbb70-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="bbb70-162">Racchiudere i nomi dei parametri facoltativi (per i parametri posizionali) tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="bbb70-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="bbb70-163">Il nome dei parametri posizionali, ad esempio il parametro Name nell'esempio seguente, non deve essere incluso nel comando.</span><span class="sxs-lookup"><span data-stu-id="bbb70-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="bbb70-164">Se un valore di parametro può contenere più valori, ad esempio un elenco di nomi nel parametro Name, aggiungere una coppia di parentesi quadre direttamente dopo il valore del parametro.</span><span class="sxs-lookup"><span data-stu-id="bbb70-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="bbb70-165">Se l'utente può scegliere tra parametri o valori di parametro, ad esempio il parametro di tipo, racchiudere le scelte tra parentesi graffe e separarle con il simbolo OR esclusivo (;).</span><span class="sxs-lookup"><span data-stu-id="bbb70-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="bbb70-166">Se il valore del parametro deve usare una formattazione specifica, ad esempio virgolette o parentesi, Mostra il formato nella sintassi.</span><span class="sxs-lookup"><span data-stu-id="bbb70-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="bbb70-167">Codifica del diagramma di sintassi XML</span><span class="sxs-lookup"><span data-stu-id="bbb70-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="bbb70-168">Il nodo della sintassi del codice XML inizia subito dopo il nodo Description, che termina con il tag \</maml: Description >.</span><span class="sxs-lookup"><span data-stu-id="bbb70-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="bbb70-169">Per informazioni sulla raccolta dei dati utilizzati nel diagramma della sintassi, vedere [raccolta di informazioni sulla sintassi](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="bbb70-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="bbb70-170">Aggiunta di un nodo della sintassi</span><span class="sxs-lookup"><span data-stu-id="bbb70-170">Adding a Syntax Node</span></span>

<span data-ttu-id="bbb70-171">Il diagramma della sintassi visualizzato nell'argomento della guida del cmdlet viene generato dai dati nel nodo Syntax del codice XML.</span><span class="sxs-lookup"><span data-stu-id="bbb70-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="bbb70-172">Il nodo della sintassi è racchiuso in una coppia se \<comando: Syntax > Tags.</span><span class="sxs-lookup"><span data-stu-id="bbb70-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="bbb70-173">Con ogni set di parametri del cmdlet racchiuso in una coppia di \<comando: syntaxitem > Tag.</span><span class="sxs-lookup"><span data-stu-id="bbb70-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="bbb70-174">Non esiste alcun limite al numero di \<comando: syntaxitem > Tag che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="bbb70-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="bbb70-175">Nell'esempio seguente viene illustrato un nodo della sintassi con nodi di elementi della sintassi per due set di parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="bbb70-176">Aggiunta del nome del cmdlet ai dati del set di parametri</span><span class="sxs-lookup"><span data-stu-id="bbb70-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="bbb70-177">Ogni set di parametri del cmdlet viene specificato in un nodo elemento della sintassi.</span><span class="sxs-lookup"><span data-stu-id="bbb70-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="bbb70-178">Ogni nodo dell'elemento della sintassi inizia con una coppia di \<maml: Name > Tag che includono il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbb70-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="bbb70-179">Nell'esempio seguente viene incluso un nodo della sintassi con nodi di elementi della sintassi per due set di parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="bbb70-180">Aggiunta di parametri</span><span class="sxs-lookup"><span data-stu-id="bbb70-180">Adding Parameters</span></span>

<span data-ttu-id="bbb70-181">Ogni parametro aggiunto al nodo elemento sintassi viene specificato in una coppia di \<comando: parametro > Tag.</span><span class="sxs-lookup"><span data-stu-id="bbb70-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="bbb70-182">È necessario disporre di una coppia di \<comando: parametro > Tag per ogni parametro incluso nel set di parametri, ad eccezione dei parametri comuni forniti da Windows PowerShell?.</span><span class="sxs-lookup"><span data-stu-id="bbb70-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="bbb70-183">Gli attributi del comando di \<di apertura: parametro > Tag determinano il modo in cui il parametro viene visualizzato nel diagramma della sintassi.</span><span class="sxs-lookup"><span data-stu-id="bbb70-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="bbb70-184">Per informazioni sugli attributi dei parametri, vedere [attributi dei parametri](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="bbb70-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="bbb70-185">Il \<comando: parametro > Tag supporta un elemento figlio \<maml: Description > il cui contenuto non viene mai visualizzato.</span><span class="sxs-lookup"><span data-stu-id="bbb70-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="bbb70-186">Le descrizioni dei parametri sono specificate nel nodo Parameter del codice XML.</span><span class="sxs-lookup"><span data-stu-id="bbb70-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="bbb70-187">Per evitare incoerenze tra le informazioni nell'elemento di sintassi Bodes e il nodo del parametro, omettere il (\<maml: Description > o lasciarlo vuoto.</span><span class="sxs-lookup"><span data-stu-id="bbb70-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="bbb70-188">Nell'esempio seguente viene incluso un nodo elemento della sintassi per un set di parametri con due parametri.</span><span class="sxs-lookup"><span data-stu-id="bbb70-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
