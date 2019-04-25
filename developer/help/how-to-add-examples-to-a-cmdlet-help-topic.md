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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083468"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="32b64-102">Come aggiungere esempi a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="32b64-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="32b64-103">Informazioni importanti informazioni sugli esempi nella Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32b64-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="32b64-104">Viste della Guida che consentono di visualizzare esempi</span><span class="sxs-lookup"><span data-stu-id="32b64-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="32b64-105">Aggiunta di un nodo di esempi</span><span class="sxs-lookup"><span data-stu-id="32b64-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="32b64-106">Aggiunta di caratteri che lo precedono</span><span class="sxs-lookup"><span data-stu-id="32b64-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="32b64-107">Aggiunta del comando</span><span class="sxs-lookup"><span data-stu-id="32b64-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="32b64-108">Aggiunta di una descrizione</span><span class="sxs-lookup"><span data-stu-id="32b64-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="32b64-109">Aggiunta dell'Output di esempio</span><span class="sxs-lookup"><span data-stu-id="32b64-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="32b64-110">Informazioni importanti informazioni sugli esempi nella Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="32b64-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="32b64-111">Elencare tutti i nomi dei parametri nel comando, anche quando i nomi dei parametri sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="32b64-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="32b64-112">Ciò consente all'utente di interpretare il comando con facilità.</span><span class="sxs-lookup"><span data-stu-id="32b64-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="32b64-113">Evitare gli alias e i nomi di parametri parziale, anche se funzionano in Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="32b64-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="32b64-114">Nella descrizione dell'esempio, spiegare il motivo per la costruzione del comando.</span><span class="sxs-lookup"><span data-stu-id="32b64-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="32b64-115">Spiegare il motivo per cui si è scelto di determinati parametri e valori e utilizzo di variabili.</span><span class="sxs-lookup"><span data-stu-id="32b64-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="32b64-116">Se il comando Usa le espressioni, li descrivono in dettaglio.</span><span class="sxs-lookup"><span data-stu-id="32b64-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="32b64-117">Se il comando Usa le proprietà e metodi di oggetti, in particolare le proprietà che non vengono visualizzati nella visualizzazione predefinita, usare l'esempio come un'opportunità informare l'utente sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="32b64-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="32b64-118">Viste della Guida che consentono di visualizzare esempi</span><span class="sxs-lookup"><span data-stu-id="32b64-118">Help Views that Display Examples</span></span>

<span data-ttu-id="32b64-119">Negli esempi vengono visualizzati solo in viste dettagliata e completa della Guida dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32b64-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="32b64-120">Aggiunta di un nodo di esempi</span><span class="sxs-lookup"><span data-stu-id="32b64-120">Adding an Examples Node</span></span>

<span data-ttu-id="32b64-121">Il codice XML seguente viene illustrato come aggiungere un nodo di esempi contenente un singolo nodo di esempio.</span><span class="sxs-lookup"><span data-stu-id="32b64-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="32b64-122">Aggiungere nodi di esempio aggiuntive per ogni esempi da includere nell'argomento.</span><span class="sxs-lookup"><span data-stu-id="32b64-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="32b64-123">Aggiunta di un titolo di esempio</span><span class="sxs-lookup"><span data-stu-id="32b64-123">Adding an Example Title</span></span>

<span data-ttu-id="32b64-124">Il codice XML seguente viene illustrato come aggiungere un titolo per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="32b64-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="32b64-125">Il titolo utilizzato per impostare l'esempio a parte di altri esempi.</span><span class="sxs-lookup"><span data-stu-id="32b64-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="32b64-126">Windows PowerShell® Usa un'intestazione standard che include un numero sequenziale di esempio.</span><span class="sxs-lookup"><span data-stu-id="32b64-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="32b64-127">Aggiunta di caratteri che lo precedono</span><span class="sxs-lookup"><span data-stu-id="32b64-127">Adding Preceding Characters</span></span>

<span data-ttu-id="32b64-128">Il codice XML seguente viene illustrato come aggiungere caratteri, ad esempio i prompt di Windows PowerShell, che vengono visualizzati immediatamente prima del comando di esempio (senza spazi intermedi).</span><span class="sxs-lookup"><span data-stu-id="32b64-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="32b64-129">Windows PowerShell® Usa il prompt dei comandi di Windows PowerShell: C:\PS&GT; &GT;.</span><span class="sxs-lookup"><span data-stu-id="32b64-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="32b64-130">Aggiunta del comando</span><span class="sxs-lookup"><span data-stu-id="32b64-130">Adding the Command</span></span>

<span data-ttu-id="32b64-131">Il codice XML seguente viene illustrato come aggiungere il comando effettivo dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="32b64-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="32b64-132">Quando si aggiunge il comando, digitare il nome completo (non usare alias) dei cmdlet e parametri.</span><span class="sxs-lookup"><span data-stu-id="32b64-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="32b64-133">Inoltre, usare caratteri minuscoli quando possibile.</span><span class="sxs-lookup"><span data-stu-id="32b64-133">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="32b64-134">Aggiunta di una descrizione</span><span class="sxs-lookup"><span data-stu-id="32b64-134">Adding a Description</span></span>

<span data-ttu-id="32b64-135">Il codice XML seguente viene illustrato come aggiungere una descrizione per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="32b64-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="32b64-136">Windows PowerShell® Usa un singolo set di \<maml: para > tag per la descrizione, anche se più \<maml: para > tag possono essere usati.</span><span class="sxs-lookup"><span data-stu-id="32b64-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="32b64-137">Aggiunta dell'Output di esempio</span><span class="sxs-lookup"><span data-stu-id="32b64-137">Adding Example Output</span></span>

<span data-ttu-id="32b64-138">Il codice XML seguente viene illustrato come aggiungere l'output del comando.</span><span class="sxs-lookup"><span data-stu-id="32b64-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="32b64-139">Le informazioni relative ai risultati del comando sono facoltativi, ma in alcuni casi è utile illustrare l'effetto dell'uso di parametri specifici.</span><span class="sxs-lookup"><span data-stu-id="32b64-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="32b64-140">Windows PowerShell® usa due set di spazio vuoto \<maml: para > tag per separare l'output del comando del comando.</span><span class="sxs-lookup"><span data-stu-id="32b64-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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