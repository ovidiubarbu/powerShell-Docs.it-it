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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083162"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="3f392-102">La scrittura Guida per i cmdlet di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f392-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="3f392-103">I cmdlet di PowerShell possono essere utili, ma, a meno che gli argomenti della Guida spiegano chiaramente il cmdlet non e come usarlo, il cmdlet non può ottenere usato o, peggio ancora, potrebbe causare frustrazione gli utenti.</span><span class="sxs-lookup"><span data-stu-id="3f392-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="3f392-104">Il formato del file della Guida cmdlet basato su XML migliora la coerenza, ma richiede molto più di grande aiuto.</span><span class="sxs-lookup"><span data-stu-id="3f392-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="3f392-105">Se è mai stata scritta Guida dei cmdlet, esaminare le indicazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="3f392-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="3f392-106">Lo schema XML necessario per creare l'argomento della Guida cmdlet è descritto nella sezione seguente.</span><span class="sxs-lookup"><span data-stu-id="3f392-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="3f392-107">Per iniziare [la creazione del File della Guida dei Cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="3f392-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="3f392-108">Questo argomento include una descrizione dei nodi XML principale.</span><span class="sxs-lookup"><span data-stu-id="3f392-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="3f392-109">Linee guida di scrittura per la Guida dei Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="3f392-110">Scriverne</span><span class="sxs-lookup"><span data-stu-id="3f392-110">Write well</span></span>
<span data-ttu-id="3f392-111">Non sostituisce un argomento ben scritto.</span><span class="sxs-lookup"><span data-stu-id="3f392-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="3f392-112">Se non si dispone di un writer professionista, trovare un writer o un editor che consentono di.</span><span class="sxs-lookup"><span data-stu-id="3f392-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="3f392-113">Un'altra alternativa consiste nel copiare il testo della Guida in Microsoft Word e usare la grammatica e ortografia controlla per migliorare il proprio lavoro.</span><span class="sxs-lookup"><span data-stu-id="3f392-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="3f392-114">Scrivere semplicemente</span><span class="sxs-lookup"><span data-stu-id="3f392-114">Write simply</span></span>
<span data-ttu-id="3f392-115">Usa semplici parole e frasi.</span><span class="sxs-lookup"><span data-stu-id="3f392-115">Use simple words and phrases.</span></span>
<span data-ttu-id="3f392-116">Evitare di terminologia.</span><span class="sxs-lookup"><span data-stu-id="3f392-116">Avoid jargon.</span></span>
<span data-ttu-id="3f392-117">Considerare che molti lettori siano dotati solo un dizionario di lingua straniera e l'argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="3f392-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="3f392-118">Scrivere in modo coerente</span><span class="sxs-lookup"><span data-stu-id="3f392-118">Write consistently</span></span>
<span data-ttu-id="3f392-119">La Guida per cmdlet correlati dovrebbe essere simile (ad esempio, get-x e set-x).</span><span class="sxs-lookup"><span data-stu-id="3f392-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="3f392-120">Usare le descrizioni di standard per i parametri standard, ad esempio **Force** e **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="3f392-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="3f392-121">(Copiarli dalla Guida per i cmdlet core.) Usare termini standard.</span><span class="sxs-lookup"><span data-stu-id="3f392-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="3f392-122">Ad esempio, usare "parametro", non "argomento" e utilizzare "cmdlet" non "command" o "command-let".</span><span class="sxs-lookup"><span data-stu-id="3f392-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="3f392-123">Avviare il riepilogo con un verbo</span><span class="sxs-lookup"><span data-stu-id="3f392-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="3f392-124">Il campo Riepilogo informa l'utente non quali cmdlet, che cos'è o come funziona.</span><span class="sxs-lookup"><span data-stu-id="3f392-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="3f392-125">Verbi di creare un'istruzione basato su attività che gli utenti vengono informati se questo cmdlet adatta alle proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="3f392-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="3f392-126">Usare verbi semplici, ad esempio "get", "Crea" e "Modifica".</span><span class="sxs-lookup"><span data-stu-id="3f392-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="3f392-127">Evitare di "set", che può essere vaga e fantasiosi parole come "Modifica".</span><span class="sxs-lookup"><span data-stu-id="3f392-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="3f392-128">Concentrarsi sugli oggetti</span><span class="sxs-lookup"><span data-stu-id="3f392-128">Focus on objects</span></span>
<span data-ttu-id="3f392-129">La maggior parte "get" cmdlet Visualizza un elemento, ma la cui funzione principale è ottenere un oggetto.</span><span class="sxs-lookup"><span data-stu-id="3f392-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="3f392-130">Il vostro aiuto, incentrata sull'oggetto, in modo che gli utenti comprendano che la visualizzazione predefinita è uno dei numerosi e che è possibile usare i metodi e proprietà dell'oggetto recuperato per loro in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="3f392-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="3f392-131">Scrivere una descrizione dettagliata</span><span class="sxs-lookup"><span data-stu-id="3f392-131">Write detailed descriptions</span></span>
<span data-ttu-id="3f392-132">Brevemente elencare tutti gli elementi che può eseguire il cmdlet nella descrizione dettagliata.</span><span class="sxs-lookup"><span data-stu-id="3f392-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="3f392-133">Se la funzione principale consiste nel modificare una proprietà, ma il cmdlet può modificare tutte le proprietà, è elencato nella descrizione dettagliata.</span><span class="sxs-lookup"><span data-stu-id="3f392-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="3f392-134">Utilizzare la sintassi tradizionale</span><span class="sxs-lookup"><span data-stu-id="3f392-134">Use conventional syntax</span></span>
<span data-ttu-id="3f392-135">Usare il formato Backus-Naur standard che è comune per Windows e la Guida della riga di comando UNIX.</span><span class="sxs-lookup"><span data-stu-id="3f392-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="3f392-136">Usare tipi di Microsoft .NET Framework per i valori dei parametri</span><span class="sxs-lookup"><span data-stu-id="3f392-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="3f392-137">I segnaposto per i valori di parametro (nella sintassi e descrizioni dei parametri) mostrano i tipi di .NET Framework degli oggetti che accetta il parametro.</span><span class="sxs-lookup"><span data-stu-id="3f392-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="3f392-138">Il team di PowerShell ha sviluppato questa convenzione per aiutare gli utenti su .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f392-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="3f392-139">Scrivere le descrizioni dei parametri completo</span><span class="sxs-lookup"><span data-stu-id="3f392-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="3f392-140">Le descrizioni dei parametri è necessario informare gli utenti delle due operazioni seguenti: il parametro non (relativo effetto) e ciò che è necessario digitare i valori dei parametri.</span><span class="sxs-lookup"><span data-stu-id="3f392-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="3f392-141">Scrittura di esempi pratici</span><span class="sxs-lookup"><span data-stu-id="3f392-141">Write practical examples</span></span>
<span data-ttu-id="3f392-142">Gli esempi devono illustrano come usare tutti i parametri, ma la cosa più importante è per mostrare come utilizzare il cmdlet di attività reali.</span><span class="sxs-lookup"><span data-stu-id="3f392-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="3f392-143">Iniziare con un semplice esempio e scrittura di esempi sempre più complessi.</span><span class="sxs-lookup"><span data-stu-id="3f392-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="3f392-144">Nell'esempio finale, Mostra come usare il cmdlet in una pipeline.</span><span class="sxs-lookup"><span data-stu-id="3f392-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="3f392-145">Usare il campo Note</span><span class="sxs-lookup"><span data-stu-id="3f392-145">Use the Notes field</span></span>
<span data-ttu-id="3f392-146">Usare il campo Note per spiegare i concetti che gli utenti devono conoscere il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3f392-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="3f392-147">È anche possibile usare note per consentire agli utenti di evitare errori comuni.</span><span class="sxs-lookup"><span data-stu-id="3f392-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="3f392-148">Evitare gli URL poiché viene modificato.</span><span class="sxs-lookup"><span data-stu-id="3f392-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="3f392-149">In alternativa, fornire le condizioni di utenti per la ricerca.</span><span class="sxs-lookup"><span data-stu-id="3f392-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="3f392-150">L'intervento dell'utente di test</span><span class="sxs-lookup"><span data-stu-id="3f392-150">Test your Help</span></span>
<span data-ttu-id="3f392-151">Testare il supporto esattamente come è testare il codice.</span><span class="sxs-lookup"><span data-stu-id="3f392-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="3f392-152">Dispone gli amici e colleghi leggere il contenuto della Guida e forniscono commenti e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="3f392-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="3f392-153">È anche possibile richiedere commenti dai newsgroup.</span><span class="sxs-lookup"><span data-stu-id="3f392-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f392-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f392-154">See Also</span></span>

 [<span data-ttu-id="3f392-155">Come creare il File della Guida dei Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="3f392-156">Come aggiungere il nome di Cmdlet e il riepilogo per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-157">Come aggiungere la descrizione dettagliata per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="3f392-158">Come aggiungere la sintassi per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-159">Come aggiungere parametri a un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="3f392-160">Come aggiungere tipi di Input a un argomento della Guida Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-161">Come aggiungere i valori restituiti per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-162">Come aggiungere le note in un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-163">Come aggiungere esempi per un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-164">Come aggiungere collegamenti correlati a un argomento della Guida del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f392-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f392-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3f392-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)