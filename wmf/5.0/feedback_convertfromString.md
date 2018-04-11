---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="ea8c8-102">Estrarre e analizzare oggetti strutturati da contenuto String</span><span class="sxs-lookup"><span data-stu-id="ea8c8-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="ea8c8-103">Sono state anche introdotte alcune funzionalità aggiuntive per il cmdlet ConvertFrom-String:</span><span class="sxs-lookup"><span data-stu-id="ea8c8-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="ea8c8-104">Rimozione della proprietà extent per il testo per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-104">Removes the extent text property by default.</span></span> <span data-ttu-id="ea8c8-105">È possibile includerla con il parametro -IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="ea8c8-106">Molte correzioni di bug per l'algoritmo di apprendimento grazie ai commenti e suggerimenti di MVP e community.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="ea8c8-107">Un nuovo parametro -UpdateTemplate per salvare i risultati dell'algoritmo di apprendimento in un commento nel file di modello.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="ea8c8-108">In questo modo il processo di apprendimento (la fase più lenta) diventa un costo una tantum.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="ea8c8-109">L'esecuzione di Convert-String con un modello che contiene l'algoritmo di apprendimento codificato è ora quasi istantanea.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="ea8c8-110">Estrarre e analizzare oggetti strutturati da contenuto String</span><span class="sxs-lookup"><span data-stu-id="ea8c8-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="ea8c8-111">In collaborazione con [Microsoft Research](http://research.microsoft.com/) è stato aggiunto il nuovo cmdlet **ConvertFrom-String**.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="ea8c8-112">Questo cmdlet supporta due modalità: l'analisi delimitata di base e l'analisi basata su esempi generati automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="ea8c8-113">L'analisi delimitata divide l'input per impostazione predefinita in corrispondenza di spazi vuoti e assegna i nomi delle proprietà ai gruppi risultanti.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="ea8c8-114">È possibile personalizzare il delimitatore:</span><span class="sxs-lookup"><span data-stu-id="ea8c8-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="ea8c8-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="ea8c8-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="ea8c8-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="ea8c8-116">P1    P2</span></span>
--    --

<span data-ttu-id="ea8c8-117">Il cmdlet supporta anche l'analisi basata su esempi generati automaticamente in base al lavoro di ricerca [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) condotto da [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="ea8c8-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="ea8c8-118">A titolo di esempio, si supponga di iniziare da una rubrica basata su testo:</span><span class="sxs-lookup"><span data-stu-id="ea8c8-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="ea8c8-119">Copiare alcuni esempi in un file, che verrà usato come modello:</span><span class="sxs-lookup"><span data-stu-id="ea8c8-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="ea8c8-120">Racchiudere i dati da estrarre tra parentesi graffe, assegnando anche un nome.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="ea8c8-121">Dato che la proprietà **Name** e le altre proprietà associate possono comparire più volte, usare un asterisco (\*) per indicare che i risultati includeranno più record, invece di estrarre una serie di proprietà in un unico record:</span><span class="sxs-lookup"><span data-stu-id="ea8c8-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="ea8c8-122">Da questo set di esempi, **ConvertFrom-String** può ora estrarre automaticamente output basato su oggetti dai file di input con una struttura analoga.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="ea8c8-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="ea8c8-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="ea8c8-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="ea8c8-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="ea8c8-125">ExtentText                     Name               City     State</span><span class="sxs-lookup"><span data-stu-id="ea8c8-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="ea8c8-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="ea8c8-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="ea8c8-127">Per apportare ulteriori modifiche ai dati nel testo estratto, la proprietà **ExtentText** acquisisce il testo non elaborato da cui è stato estratto il record.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="ea8c8-128">Per fornire commenti e suggerimenti su questa funzionalità o per condividere contenuto per cui risulta problematica la scrittura di esempi, inviare un messaggio di posta elettronica a <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="ea8c8-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>