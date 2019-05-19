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
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855123"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="a785d-102">Come aggiungere esempi a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="a785d-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="a785d-103">Informazioni importanti informazioni sugli esempi nella Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a785d-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="a785d-104">Elencare tutti i nomi dei parametri nel comando, anche quando i nomi dei parametri sono facoltativi.</span><span class="sxs-lookup"><span data-stu-id="a785d-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="a785d-105">Ciò consente all'utente di interpretare il comando con facilità.</span><span class="sxs-lookup"><span data-stu-id="a785d-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="a785d-106">Evitare gli alias e i nomi di parametri parziale, anche se funzionano in Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="a785d-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="a785d-107">Nella descrizione dell'esempio, spiegare il motivo per la costruzione del comando.</span><span class="sxs-lookup"><span data-stu-id="a785d-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="a785d-108">Spiegare il motivo per cui si è scelto di determinati parametri e valori e utilizzo di variabili.</span><span class="sxs-lookup"><span data-stu-id="a785d-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="a785d-109">Se il comando Usa le espressioni, li descrivono in dettaglio.</span><span class="sxs-lookup"><span data-stu-id="a785d-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="a785d-110">Se il comando Usa le proprietà e metodi di oggetti, in particolare le proprietà che non vengono visualizzati nella visualizzazione predefinita, usare l'esempio come un'opportunità informare l'utente sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a785d-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="a785d-111">Viste della Guida che consentono di visualizzare esempi</span><span class="sxs-lookup"><span data-stu-id="a785d-111">Help Views that Display Examples</span></span>

<span data-ttu-id="a785d-112">Negli esempi vengono visualizzati solo in viste dettagliata e completa della Guida dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a785d-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="a785d-113">Aggiunta di un nodo di esempi</span><span class="sxs-lookup"><span data-stu-id="a785d-113">Adding an Examples Node</span></span>

<span data-ttu-id="a785d-114">Il codice XML seguente viene illustrato come aggiungere un nodo di esempi contenente un singolo nodo di esempio.</span><span class="sxs-lookup"><span data-stu-id="a785d-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="a785d-115">Aggiungere nodi di esempio aggiuntive per ogni esempi da includere nell'argomento.</span><span class="sxs-lookup"><span data-stu-id="a785d-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="a785d-116">Aggiunta di un titolo di esempio</span><span class="sxs-lookup"><span data-stu-id="a785d-116">Adding an Example Title</span></span>

<span data-ttu-id="a785d-117">Il codice XML seguente viene illustrato come aggiungere un titolo per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="a785d-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="a785d-118">Il titolo utilizzato per impostare l'esempio a parte di altri esempi.</span><span class="sxs-lookup"><span data-stu-id="a785d-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="a785d-119">Windows PowerShell® Usa un'intestazione standard che include un numero sequenziale di esempio.</span><span class="sxs-lookup"><span data-stu-id="a785d-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="a785d-120">Aggiunta di caratteri che lo precedono</span><span class="sxs-lookup"><span data-stu-id="a785d-120">Adding Preceding Characters</span></span>

<span data-ttu-id="a785d-121">Il codice XML seguente viene illustrato come aggiungere caratteri, ad esempio i prompt di Windows PowerShell, che vengono visualizzati immediatamente prima del comando di esempio (senza spazi intermedi).</span><span class="sxs-lookup"><span data-stu-id="a785d-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="a785d-122">Windows PowerShell® Usa il prompt dei comandi di Windows PowerShell: C:\PS&GT; &GT;.</span><span class="sxs-lookup"><span data-stu-id="a785d-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="a785d-123">Aggiunta del comando</span><span class="sxs-lookup"><span data-stu-id="a785d-123">Adding the Command</span></span>

<span data-ttu-id="a785d-124">Il codice XML seguente viene illustrato come aggiungere il comando effettivo dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="a785d-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="a785d-125">Quando si aggiunge il comando, digitare il nome completo (non usare alias) dei cmdlet e parametri.</span><span class="sxs-lookup"><span data-stu-id="a785d-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="a785d-126">Inoltre, usare caratteri minuscoli quando possibile.</span><span class="sxs-lookup"><span data-stu-id="a785d-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="a785d-127">Aggiunta di una descrizione</span><span class="sxs-lookup"><span data-stu-id="a785d-127">Adding a Description</span></span>

<span data-ttu-id="a785d-128">Il codice XML seguente viene illustrato come aggiungere una descrizione per l'esempio.</span><span class="sxs-lookup"><span data-stu-id="a785d-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="a785d-129">Windows PowerShell® Usa un singolo set di \<maml: para > tag per la descrizione, anche se più \<maml: para > tag possono essere usati.</span><span class="sxs-lookup"><span data-stu-id="a785d-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="a785d-130">Aggiunta dell'Output di esempio</span><span class="sxs-lookup"><span data-stu-id="a785d-130">Adding Example Output</span></span>

<span data-ttu-id="a785d-131">Il codice XML seguente viene illustrato come aggiungere l'output del comando.</span><span class="sxs-lookup"><span data-stu-id="a785d-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="a785d-132">Le informazioni relative ai risultati del comando sono facoltativi, ma in alcuni casi è utile illustrare l'effetto dell'uso di parametri specifici.</span><span class="sxs-lookup"><span data-stu-id="a785d-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="a785d-133">Windows PowerShell® usa due set di spazio vuoto \<maml: para > tag per separare l'output del comando del comando.</span><span class="sxs-lookup"><span data-stu-id="a785d-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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