---
title: Scrittura della Guida per i cmdlet di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361070"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="6602c-102">Scrittura della Guida per i cmdlet di PowerShell</span><span class="sxs-lookup"><span data-stu-id="6602c-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="6602c-103">I cmdlet di PowerShell possono essere utili, ma a meno che gli argomenti della guida non spieghino chiaramente cosa fa il cmdlet e come usarlo, è possibile che il cmdlet non venga usato o, anche peggio, che possa frustrare gli utenti.</span><span class="sxs-lookup"><span data-stu-id="6602c-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="6602c-104">Il formato di file della guida del cmdlet basato su XML migliora la coerenza, ma è molto utile.</span><span class="sxs-lookup"><span data-stu-id="6602c-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="6602c-105">Se non è mai stata scritta la guida dei cmdlet, consultare le linee guida seguenti.</span><span class="sxs-lookup"><span data-stu-id="6602c-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="6602c-106">La XML Schema necessaria per creare l'argomento della guida del cmdlet è descritta nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="6602c-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="6602c-107">Iniziare con [la creazione del file della guida del cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="6602c-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="6602c-108">Questo argomento include una descrizione dei nodi XML di primo livello.</span><span class="sxs-lookup"><span data-stu-id="6602c-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="6602c-109">Guida alla scrittura della Guida per i cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="6602c-110">Scrivi bene</span><span class="sxs-lookup"><span data-stu-id="6602c-110">Write well</span></span>
<span data-ttu-id="6602c-111">Niente sostituisce un argomento ben scritto.</span><span class="sxs-lookup"><span data-stu-id="6602c-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="6602c-112">Se non si è un writer professionale, trovare un writer o un editor per aiutarti.</span><span class="sxs-lookup"><span data-stu-id="6602c-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="6602c-113">Un'altra alternativa consiste nel copiare il testo della Guida in Microsoft Word e usare i controlli di grammatica e ortografia per migliorare il lavoro.</span><span class="sxs-lookup"><span data-stu-id="6602c-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="6602c-114">Scrivi semplicemente</span><span class="sxs-lookup"><span data-stu-id="6602c-114">Write simply</span></span>
<span data-ttu-id="6602c-115">Usare parole e frasi semplici.</span><span class="sxs-lookup"><span data-stu-id="6602c-115">Use simple words and phrases.</span></span>
<span data-ttu-id="6602c-116">Evitare il gergo.</span><span class="sxs-lookup"><span data-stu-id="6602c-116">Avoid jargon.</span></span>
<span data-ttu-id="6602c-117">Tenere presente che molti Reader sono dotati solo di un dizionario in lingua straniera e dell'argomento della guida.</span><span class="sxs-lookup"><span data-stu-id="6602c-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="6602c-118">Scrittura coerente</span><span class="sxs-lookup"><span data-stu-id="6602c-118">Write consistently</span></span>
<span data-ttu-id="6602c-119">La guida per i cmdlet correlati dovrebbe essere simile, ad esempio Get-x e set-x.</span><span class="sxs-lookup"><span data-stu-id="6602c-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="6602c-120">Usare le descrizioni standard per i parametri standard, ad esempio **Force** e **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="6602c-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="6602c-121">(Copiarli dalla guida per i cmdlet di base). Usare i termini standard.</span><span class="sxs-lookup"><span data-stu-id="6602c-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="6602c-122">Ad esempio, usare "Parameter", non "argument" e usare "cmdlet" non "Command" o "command-let".</span><span class="sxs-lookup"><span data-stu-id="6602c-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="6602c-123">Avviare la sintrama con un verbo</span><span class="sxs-lookup"><span data-stu-id="6602c-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="6602c-124">Il campo Sinossi informa l'utente dell'operazione eseguita dal cmdlet, non di come è o come funziona.</span><span class="sxs-lookup"><span data-stu-id="6602c-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="6602c-125">I verbi creano un'istruzione basata su attività che informa gli utenti se il cmdlet soddisfa i requisiti.</span><span class="sxs-lookup"><span data-stu-id="6602c-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="6602c-126">Usare verbi semplici come "Get", "create" e "Change".</span><span class="sxs-lookup"><span data-stu-id="6602c-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="6602c-127">Evitare "set", che può essere un testo vago e un'immaginazione come "Modify".</span><span class="sxs-lookup"><span data-stu-id="6602c-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="6602c-128">Concentrarsi sugli oggetti</span><span class="sxs-lookup"><span data-stu-id="6602c-128">Focus on objects</span></span>
<span data-ttu-id="6602c-129">Per la maggior parte dei cmdlet "Get" viene visualizzato un elemento, ma la funzione principale è quella di ottenere un oggetto.</span><span class="sxs-lookup"><span data-stu-id="6602c-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="6602c-130">Nella Guida concentrarsi sull'oggetto, in modo che gli utenti capiscano che la visualizzazione predefinita è una delle numerose e che possono usare i metodi e le proprietà dell'oggetto recuperato in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="6602c-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="6602c-131">Scrivi descrizioni dettagliate</span><span class="sxs-lookup"><span data-stu-id="6602c-131">Write detailed descriptions</span></span>
<span data-ttu-id="6602c-132">Elencare brevemente tutti gli elementi che il cmdlet può eseguire nella descrizione dettagliata.</span><span class="sxs-lookup"><span data-stu-id="6602c-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="6602c-133">Se la funzione principale prevede la modifica di una proprietà, ma il cmdlet può modificare tutte le proprietà, elencarlo nella descrizione dettagliata.</span><span class="sxs-lookup"><span data-stu-id="6602c-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="6602c-134">USA sintassi convenzionale</span><span class="sxs-lookup"><span data-stu-id="6602c-134">Use conventional syntax</span></span>
<span data-ttu-id="6602c-135">Usare il formato Backus-Naur standard comune per la guida della riga di comando di Windows e UNIX.</span><span class="sxs-lookup"><span data-stu-id="6602c-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="6602c-136">Usare Microsoft .NET tipi di Framework per i valori dei parametri</span><span class="sxs-lookup"><span data-stu-id="6602c-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="6602c-137">I segnaposto per i valori dei parametri (nella sintassi e nelle descrizioni dei parametri) mostrano i tipi di .NET Framework degli oggetti accettati dal parametro.</span><span class="sxs-lookup"><span data-stu-id="6602c-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="6602c-138">Il team di PowerShell ha sviluppato questa convenzione per aiutare gli utenti a insegnare i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6602c-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="6602c-139">Scrivi descrizioni dei parametri completi</span><span class="sxs-lookup"><span data-stu-id="6602c-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="6602c-140">Le descrizioni dei parametri devono informare gli utenti di due cose: cosa fa il parametro (effetto) e cosa devono digitare per i valori dei parametri.</span><span class="sxs-lookup"><span data-stu-id="6602c-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="6602c-141">Scrivi esempi pratici</span><span class="sxs-lookup"><span data-stu-id="6602c-141">Write practical examples</span></span>
<span data-ttu-id="6602c-142">Gli esempi illustrano come usare tutti i parametri, ma la cosa più importante è illustrare come usare il cmdlet in attività reali.</span><span class="sxs-lookup"><span data-stu-id="6602c-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="6602c-143">Inizia con un semplice esempio e Scrivi esempi sempre più complessi.</span><span class="sxs-lookup"><span data-stu-id="6602c-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="6602c-144">Nell'esempio finale, Mostra come usare il cmdlet in una pipeline.</span><span class="sxs-lookup"><span data-stu-id="6602c-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="6602c-145">Usare il campo note</span><span class="sxs-lookup"><span data-stu-id="6602c-145">Use the Notes field</span></span>
<span data-ttu-id="6602c-146">Usare il campo note per spiegare i concetti necessari agli utenti per comprendere il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6602c-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="6602c-147">È inoltre possibile utilizzare note per aiutare gli utenti a evitare errori comuni.</span><span class="sxs-lookup"><span data-stu-id="6602c-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="6602c-148">Evitare gli URL Man mano che cambiano.</span><span class="sxs-lookup"><span data-stu-id="6602c-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="6602c-149">Fornire invece i termini degli utenti per la ricerca.</span><span class="sxs-lookup"><span data-stu-id="6602c-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="6602c-150">Testare la guida</span><span class="sxs-lookup"><span data-stu-id="6602c-150">Test your Help</span></span>
<span data-ttu-id="6602c-151">Testare la guida esattamente come si esegue il test del codice.</span><span class="sxs-lookup"><span data-stu-id="6602c-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="6602c-152">Chiedere a amici e colleghi di leggere il contenuto della guida e fornire commenti e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="6602c-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="6602c-153">È anche possibile richiedere commenti e suggerimenti da newsgroup.</span><span class="sxs-lookup"><span data-stu-id="6602c-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="6602c-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6602c-154">See Also</span></span>

 [<span data-ttu-id="6602c-155">Come creare il file della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="6602c-156">Come aggiungere il nome del cmdlet e la sintrama a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-157">Come aggiungere la descrizione dettagliata a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="6602c-158">Come aggiungere la sintassi a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-159">Come aggiungere parametri a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="6602c-160">Come aggiungere tipi di input a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-161">Come aggiungere valori restituiti a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-162">Come aggiungere note a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-163">Come aggiungere esempi a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-164">Come aggiungere collegamenti correlati a un argomento della guida del cmdlet</span><span class="sxs-lookup"><span data-stu-id="6602c-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="6602c-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6602c-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)