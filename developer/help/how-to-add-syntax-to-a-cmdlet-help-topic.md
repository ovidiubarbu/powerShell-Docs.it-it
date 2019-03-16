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
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054612"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="1c61e-102">Come aggiungere la sintassi a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c61e-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="1c61e-103">Attributi dei parametri</span><span class="sxs-lookup"><span data-stu-id="1c61e-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="1c61e-104">Attributi del valore di parametro</span><span class="sxs-lookup"><span data-stu-id="1c61e-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="1c61e-105">Informazioni sulla sintassi di raccolta</span><span class="sxs-lookup"><span data-stu-id="1c61e-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="1c61e-106">Il diagramma della sintassi XML di codifica</span><span class="sxs-lookup"><span data-stu-id="1c61e-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="1c61e-107">Aspetti da considerare il diagramma della sintassi nella Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c61e-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="1c61e-108">Prima di avviare il codice XML per il diagramma della sintassi nel file della Guida cmdlet del codice, leggere questa sezione per ottenere un quadro preciso del tipo di dati che è necessario specificare, ad esempio gli attributi di parametro e la modalità di visualizzazione che i dati nel diagramma della sintassi...</span><span class="sxs-lookup"><span data-stu-id="1c61e-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="1c61e-109">Attributi dei parametri</span><span class="sxs-lookup"><span data-stu-id="1c61e-109">Parameter Attributes</span></span>

- <span data-ttu-id="1c61e-110">Obbligatoria</span><span class="sxs-lookup"><span data-stu-id="1c61e-110">Required</span></span>

  - <span data-ttu-id="1c61e-111">Se true, il parametro deve essere presente in tutti i comandi che usano il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="1c61e-112">Se false, il parametro è facoltativo in tutti i comandi che usano il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="1c61e-113">Posizione</span><span class="sxs-lookup"><span data-stu-id="1c61e-113">Position</span></span>

  - <span data-ttu-id="1c61e-114">Se un nome, il nome di parametro è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1c61e-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="1c61e-115">Se è posizionale, il nome del parametro è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c61e-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="1c61e-116">Quando viene omesso, il valore del parametro deve essere nella posizione specificata nel comando.</span><span class="sxs-lookup"><span data-stu-id="1c61e-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="1c61e-117">Ad esempio, se il valore è posizione = "1", il valore del parametro deve essere il primo o l'unico valore di parametro nel comando senza nome.</span><span class="sxs-lookup"><span data-stu-id="1c61e-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="1c61e-118">Input della pipeline</span><span class="sxs-lookup"><span data-stu-id="1c61e-118">Pipeline Input</span></span>

  - <span data-ttu-id="1c61e-119">Se true (ByValue), è possibile inviare input tramite pipe al parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="1c61e-120">L'input è associato con ("associazione a") il parametro anche se il nome della proprietà e il tipo di oggetto non corrispondono al tipo previsto.</span><span class="sxs-lookup"><span data-stu-id="1c61e-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="1c61e-121">Il comando di Windows PowerShell? i componenti di associazione di parametro tenta di convertire l'input nel tipo corretto e il comando solo quando il tipo non può essere convertito.</span><span class="sxs-lookup"><span data-stu-id="1c61e-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="1c61e-122">Per valore, è possibile associare un solo parametro in un set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="1c61e-123">Se true (ByPropertyName), è possibile inviare input tramite pipe al parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="1c61e-124">Tuttavia, l'input è associato il parametro solo quando il nome del parametro corrisponde al nome di una proprietà dell'oggetto di input.</span><span class="sxs-lookup"><span data-stu-id="1c61e-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="1c61e-125">Ad esempio, se è il nome del parametro `Path`, gli oggetti inviati tramite pipe al cmdlet sono associati a tale parametro solo quando l'oggetto ha una proprietà denominata percorso.</span><span class="sxs-lookup"><span data-stu-id="1c61e-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="1c61e-126">Se true (ByValue, ByPropertyName), è possibile inviare input tramite pipe al parametro dal nome della proprietà o dal valore.</span><span class="sxs-lookup"><span data-stu-id="1c61e-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="1c61e-127">Per valore, è possibile associare un solo parametro in un set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="1c61e-128">Se false, è possibile inviare tramite pipe di input per questo parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="1c61e-129">Caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="1c61e-129">Globbing</span></span>

  - <span data-ttu-id="1c61e-130">Se true, il testo digitato dall'utente per il valore del parametro può includere caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="1c61e-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="1c61e-131">Se false, il testo digitato dall'utente per il valore del parametro non può includere caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="1c61e-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="1c61e-132">Attributi del valore di parametro</span><span class="sxs-lookup"><span data-stu-id="1c61e-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="1c61e-133">Obbligatoria</span><span class="sxs-lookup"><span data-stu-id="1c61e-133">Required</span></span>

  - <span data-ttu-id="1c61e-134">Se true, il valore specificato deve essere utilizzato ogni volta che tramite il parametro in un comando.</span><span class="sxs-lookup"><span data-stu-id="1c61e-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="1c61e-135">Se false, il valore del parametro è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="1c61e-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="1c61e-136">In genere, un valore è facoltativo solo se è uno dei diversi valori validi per un parametro, ad esempio in un tipo enumerato.</span><span class="sxs-lookup"><span data-stu-id="1c61e-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="1c61e-137">L'attributo obbligatorio di un valore di parametro è diverso dall'attributo di un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="1c61e-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="1c61e-138">L'attributo obbligatorio di un parametro indica se il parametro (e il relativo valore) deve essere inclusi quando si richiama il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c61e-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="1c61e-139">Al contrario, l'attributo obbligatorio di un valore del parametro viene utilizzato solo quando il parametro è incluso nel comando.</span><span class="sxs-lookup"><span data-stu-id="1c61e-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="1c61e-140">Indica se è necessario usare quel valore specifico con il parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="1c61e-141">In genere, sono necessari i valori dei parametri sono segnaposto e i valori dei parametri sono valori letterali non sono necessari, perché sono uno dei diversi valori che potrebbero essere usati con il parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="1c61e-142">Informazioni sulla sintassi di raccolta</span><span class="sxs-lookup"><span data-stu-id="1c61e-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="1c61e-143">Iniziare con il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c61e-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="1c61e-144">Elencare tutti i parametri del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c61e-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="1c61e-145">Digitare un trattino (anche noto come "trattino" o "segno" (ASCII 45) prima di ogni nome di parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="1c61e-146">Separare i parametri in set di parametri (alcuni cmdlet potrebbe avere un solo parametro impostato).</span><span class="sxs-lookup"><span data-stu-id="1c61e-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="1c61e-147">In questo esempio di Get-Tech cmdlet dispone di due set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="1c61e-148">Avviare ogni parametro impostato con il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c61e-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="1c61e-149">Elencare il set prima di tutto di parametri predefinito.</span><span class="sxs-lookup"><span data-stu-id="1c61e-149">List the default parameter set first.</span></span> <span data-ttu-id="1c61e-150">Il parametro predefinito è specificato dalla classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c61e-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="1c61e-151">Per ogni set di parametri, il parametro univoco primo elenco, a meno che non vi sono parametri posizionali devono trovarsi all'inizio.</span><span class="sxs-lookup"><span data-stu-id="1c61e-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="1c61e-152">Nell'esempio precedente, i nome e ID i parametri sono parametri univoci per i due set di parametri (ogni set di parametri deve avere un parametro che è univoco per tale set di parametri).</span><span class="sxs-lookup"><span data-stu-id="1c61e-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="1c61e-153">Questo rende più semplice per gli utenti identificare il parametro è necessario fornire per il parametro impostato.</span><span class="sxs-lookup"><span data-stu-id="1c61e-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="1c61e-154">Elencare i parametri nell'ordine in cui appaiono nel comando.</span><span class="sxs-lookup"><span data-stu-id="1c61e-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="1c61e-155">Se l'ordine non è rilevante, elencare i parametri correlati tra loro o elencare innanzitutto i parametri usati più di frequente.</span><span class="sxs-lookup"><span data-stu-id="1c61e-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="1c61e-156">Assicurarsi di elencare i parametri WhatIf and Confirm se il cmdlet supporta ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="1c61e-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="1c61e-157">Non elencano i parametri comuni (ad esempio Verbose, Debug ed ErrorAction) nel diagramma di sintassi.</span><span class="sxs-lookup"><span data-stu-id="1c61e-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="1c61e-158">Il `Get-Help` cmdlet aggiunge le informazioni per l'utente quando questo viene visualizzato l'argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="1c61e-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="1c61e-159">Aggiungere i valori dei parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-159">Add the parameter values.</span></span> <span data-ttu-id="1c61e-160">In Windows PowerShell?, i valori dei parametri sono rappresentati in base al tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="1c61e-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="1c61e-161">Il nome del tipo può tuttavia essere abbreviato, ad esempio "string" per System. String.</span><span class="sxs-lookup"><span data-stu-id="1c61e-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="1c61e-162">Abbreviare i tipi, purché il significato è chiaro, ad esempio "string" per System. String e "int" per System.Int32.</span><span class="sxs-lookup"><span data-stu-id="1c61e-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="1c61e-163">Elencare tutti i valori delle enumerazioni, ad esempio il parametro - type nell'esempio precedente, che può essere impostata su "basic" o "avanzata".</span><span class="sxs-lookup"><span data-stu-id="1c61e-163">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="1c61e-164">Passare i parametri, ad esempio - elenco dell'esempio precedente, non dispongono di valori.</span><span class="sxs-lookup"><span data-stu-id="1c61e-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="1c61e-165">Aggiungere i valori dei parametri che sono segnaposto, rispetto ai valori dei parametri sono valori letterali parentesi angolari.</span><span class="sxs-lookup"><span data-stu-id="1c61e-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="1c61e-166">Racchiudere i parametri facoltativi e i valori mostrati tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="1c61e-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="1c61e-167">Parentesi quadre, racchiudere i nomi dei parametri facoltativi (per i parametri posizionali).</span><span class="sxs-lookup"><span data-stu-id="1c61e-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="1c61e-168">Il nome per i parametri posizionali, ad esempio il parametro Name nell'esempio seguente, non è possibile includere nel comando.</span><span class="sxs-lookup"><span data-stu-id="1c61e-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="1c61e-169">Se un valore di parametro può contenere più valori, ad esempio un elenco di nomi nel parametro Name, aggiungere una coppia di parentesi quadre seguono il valore del parametro.</span><span class="sxs-lookup"><span data-stu-id="1c61e-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="1c61e-170">Se l'utente può scegliere tra parametri o valori di parametro, ad esempio il parametro di tipo, racchiudere le scelte tra parentesi graffe e separarle con symbol(;) di OR esclusivo.</span><span class="sxs-lookup"><span data-stu-id="1c61e-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="1c61e-171">Se il valore del parametro deve utilizzare una formattazione specifica, ad esempio virgolette doppie o parentesi tonde, mostrare il formato nella sintassi.</span><span class="sxs-lookup"><span data-stu-id="1c61e-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="1c61e-172">Il diagramma della sintassi XML di codifica</span><span class="sxs-lookup"><span data-stu-id="1c61e-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="1c61e-173">Il nodo di sintassi del XML inizia immediatamente dopo il nodo di description, che termina con il \</maml:description > tag.</span><span class="sxs-lookup"><span data-stu-id="1c61e-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="1c61e-174">Per informazioni sulla raccolta dei dati utilizzati nel diagramma della sintassi, vedere [informazioni sulla sintassi di raccolta](#Gathering-Syntax-Information).</span><span class="sxs-lookup"><span data-stu-id="1c61e-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="1c61e-175">Aggiunta di un nodo di sintassi</span><span class="sxs-lookup"><span data-stu-id="1c61e-175">Adding a Syntax Node</span></span>

<span data-ttu-id="1c61e-176">Il diagramma della sintassi visualizzato nell'argomento della Guida cmdlet viene generato dai dati nel nodo sintassi del XML.</span><span class="sxs-lookup"><span data-stu-id="1c61e-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="1c61e-177">Il nodo della sintassi è racchiuso tra una coppia se \<: sintassi del comando > tag.</span><span class="sxs-lookup"><span data-stu-id="1c61e-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="1c61e-178">Con ogni set di parametri del cmdlet racchiuso tra una coppia di \<comando: syntaxitem > tag.</span><span class="sxs-lookup"><span data-stu-id="1c61e-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="1c61e-179">Non sono previsti limiti al numero di \<comando: syntaxitem > tag che è possibile aggiungere.</span><span class="sxs-lookup"><span data-stu-id="1c61e-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="1c61e-180">L'esempio seguente illustra un nodo di sintassi che dispone di nodi di elemento di sintassi per due set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="1c61e-181">Aggiunta del nome del Cmdlet al parametro del Set di dati</span><span class="sxs-lookup"><span data-stu-id="1c61e-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="1c61e-182">Ogni set di parametri del cmdlet è specificato in un nodo di elemento di sintassi.</span><span class="sxs-lookup"><span data-stu-id="1c61e-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="1c61e-183">Ogni nodo di elemento di sintassi inizia con una coppia di \<maml:name > tag che includono il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c61e-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="1c61e-184">L'esempio seguente include un nodo di sintassi che dispone di nodi di elemento di sintassi per due set di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="1c61e-185">Aggiunta di parametri</span><span class="sxs-lookup"><span data-stu-id="1c61e-185">Adding Parameters</span></span>

<span data-ttu-id="1c61e-186">Ogni parametro aggiunto al nodo di elemento di sintassi viene specificato all'interno di una coppia di \<: parametro del comando > tag.</span><span class="sxs-lookup"><span data-stu-id="1c61e-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="1c61e-187">Necessaria una coppia di \<: parametro del comando > tag per ogni parametro incluso nel set di parametri, fatta eccezione per i parametri comuni fornite da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c61e-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="1c61e-188">Gli attributi dell'apertura \<: parametro del comando > tag determinano il modo in cui il parametro viene visualizzato nel diagramma della sintassi.</span><span class="sxs-lookup"><span data-stu-id="1c61e-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="1c61e-189">Per informazioni sugli attributi di parametro, vedere [attributi di parametro](#Parameter-Attributes).</span><span class="sxs-lookup"><span data-stu-id="1c61e-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="1c61e-190">Il \<: parametro del comando > tag supporta un elemento figlio \<maml:description > il cui contenuto non viene mai visualizzato.</span><span class="sxs-lookup"><span data-stu-id="1c61e-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="1c61e-191">Le descrizioni dei parametri vengono specificati nel nodo parametro del codice XML.</span><span class="sxs-lookup"><span data-stu-id="1c61e-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="1c61e-192">Per evitare le incoerenze tra le informazioni nell'elemento di sintassi bodes e il nodo di parametro, omettere il (\<maml:description > o lasciarlo vuoto.</span><span class="sxs-lookup"><span data-stu-id="1c61e-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="1c61e-193">L'esempio seguente include un nodo di elemento di sintassi per un set con due parametri di parametri.</span><span class="sxs-lookup"><span data-stu-id="1c61e-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
