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
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="154e2-102">Come aggiungere esempi a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="154e2-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="154e2-103">Informazioni sugli esempi nella Guida dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="154e2-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="154e2-104">Elencare tutti i nomi di parametro nel comando, anche quando i nomi dei parametri sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="154e2-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="154e2-105">Questo consente all'utente di interpretare il comando con facilità.</span><span class="sxs-lookup"><span data-stu-id="154e2-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="154e2-106">Evitare gli alias e i nomi di parametro parziali, anche se funzionano in® di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="154e2-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="154e2-107">Nella descrizione dell'esempio, spiegare il razionale per la costruzione del comando.</span><span class="sxs-lookup"><span data-stu-id="154e2-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="154e2-108">Spiegare il motivo per cui si sono scelti parametri e valori specifici e come usare le variabili.</span><span class="sxs-lookup"><span data-stu-id="154e2-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="154e2-109">Se il comando usa espressioni, spiegarle in dettaglio.</span><span class="sxs-lookup"><span data-stu-id="154e2-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="154e2-110">Se il comando USA proprietà e metodi di oggetti, in particolare le proprietà che non vengono visualizzate nella visualizzazione predefinita, usare l'esempio come opportunità per informare l'utente sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="154e2-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="154e2-111">Viste della guida che visualizzano esempi</span><span class="sxs-lookup"><span data-stu-id="154e2-111">Help Views that Display Examples</span></span>

<span data-ttu-id="154e2-112">Gli esempi vengono visualizzati solo nella visualizzazione dettagliata e completa della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="154e2-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="154e2-113">Aggiunta di un nodo esempi</span><span class="sxs-lookup"><span data-stu-id="154e2-113">Adding an Examples Node</span></span>

<span data-ttu-id="154e2-114">Nel codice XML seguente viene illustrato come aggiungere un nodo esempi contenente un singolo nodo di esempio.</span><span class="sxs-lookup"><span data-stu-id="154e2-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="154e2-115">Aggiungere altri nodi di esempio per ogni esempio che si desidera includere nell'argomento.</span><span class="sxs-lookup"><span data-stu-id="154e2-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="154e2-116">Aggiunta di un titolo di esempio</span><span class="sxs-lookup"><span data-stu-id="154e2-116">Adding an Example Title</span></span>

<span data-ttu-id="154e2-117">Nel codice XML seguente viene illustrato come aggiungere un titolo per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="154e2-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="154e2-118">Il titolo viene usato per impostare l'esempio oltre ad altri esempi.</span><span class="sxs-lookup"><span data-stu-id="154e2-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="154e2-119">Windows PowerShell® usa un'intestazione standard che include un numero di esempio sequenziale.</span><span class="sxs-lookup"><span data-stu-id="154e2-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="154e2-120">Aggiunta di caratteri precedenti</span><span class="sxs-lookup"><span data-stu-id="154e2-120">Adding Preceding Characters</span></span>

<span data-ttu-id="154e2-121">Nel codice XML seguente viene illustrato come aggiungere caratteri, ad esempio il prompt di Windows PowerShell, che vengono visualizzati immediatamente prima del comando di esempio (senza spazi intermedi).</span><span class="sxs-lookup"><span data-stu-id="154e2-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="154e2-122">Windows PowerShell® usa il prompt di Windows PowerShell: C:\PS >.</span><span class="sxs-lookup"><span data-stu-id="154e2-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="154e2-123">Aggiunta del comando</span><span class="sxs-lookup"><span data-stu-id="154e2-123">Adding the Command</span></span>

<span data-ttu-id="154e2-124">Nel codice XML seguente viene illustrato come aggiungere il comando effettivo dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="154e2-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="154e2-125">Quando si aggiunge il comando, digitare l'intero nome (non usare alias) di cmdlet e parametri.</span><span class="sxs-lookup"><span data-stu-id="154e2-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="154e2-126">Inoltre, quando possibile, utilizzare caratteri minuscoli.</span><span class="sxs-lookup"><span data-stu-id="154e2-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="154e2-127">Aggiunta di una descrizione</span><span class="sxs-lookup"><span data-stu-id="154e2-127">Adding a Description</span></span>

<span data-ttu-id="154e2-128">Nel codice XML seguente viene illustrato come aggiungere una descrizione per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="154e2-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="154e2-129">Windows PowerShell® usa un singolo set di tag \<maml: para > per la descrizione, anche se è possibile usare più tag \<maml: para >.</span><span class="sxs-lookup"><span data-stu-id="154e2-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="154e2-130">Aggiunta dell'output di esempio</span><span class="sxs-lookup"><span data-stu-id="154e2-130">Adding Example Output</span></span>

<span data-ttu-id="154e2-131">Nel codice XML seguente viene illustrato come aggiungere l'output del comando.</span><span class="sxs-lookup"><span data-stu-id="154e2-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="154e2-132">Le informazioni sui risultati del comando sono facoltative, ma in alcuni casi è utile illustrare l'effetto dell'utilizzo di parametri specifici.</span><span class="sxs-lookup"><span data-stu-id="154e2-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="154e2-133">Windows PowerShell® usa due set di tag blank \<maml: para > per separare l'output del comando dal comando.</span><span class="sxs-lookup"><span data-stu-id="154e2-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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