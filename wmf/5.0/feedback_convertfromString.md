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
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Estrarre e analizzare oggetti strutturati da contenuto String
Sono state anche introdotte alcune funzionalità aggiuntive per il cmdlet ConvertFrom-String:

-   Rimozione della proprietà extent per il testo per impostazione predefinita. È possibile includerla con il parametro -IncludeExtent.

-   Molte correzioni di bug per l'algoritmo di apprendimento grazie ai commenti e suggerimenti di MVP e community.

-   Un nuovo parametro -UpdateTemplate per salvare i risultati dell'algoritmo di apprendimento in un commento nel file di modello. In questo modo il processo di apprendimento (la fase più lenta) diventa un costo una tantum. L'esecuzione di Convert-String con un modello che contiene l'algoritmo di apprendimento codificato è ora quasi istantanea.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Estrarre e analizzare oggetti strutturati da contenuto String
----------------------------------------------------------

In collaborazione con [Microsoft Research](http://research.microsoft.com/) è stato aggiunto il nuovo cmdlet **ConvertFrom-String**.

Questo cmdlet supporta due modalità: l'analisi delimitata di base e l'analisi basata su esempi generati automaticamente.

L'analisi delimitata divide l'input per impostazione predefinita in corrispondenza di spazi vuoti e assegna i nomi delle proprietà ai gruppi risultanti. È possibile personalizzare il delimitatore:

> 1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto

P1    P2
--    --

Il cmdlet supporta anche l'analisi basata su esempi generati automaticamente in base al lavoro di ricerca [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) condotto da [Microsoft Research](http://research.microsoft.com).

A titolo di esempio, si supponga di iniziare da una rubrica basata su testo:

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

Copiare alcuni esempi in un file, che verrà usato come modello:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



Racchiudere i dati da estrarre tra parentesi graffe, assegnando anche un nome. Dato che la proprietà **Name** e le altre proprietà associate possono comparire più volte, usare un asterisco (\*) per indicare che i risultati includeranno più record, invece di estrarre una serie di proprietà in un unico record:

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

Da questo set di esempi, **ConvertFrom-String** può ora estrarre automaticamente output basato su oggetti dai file di input con una struttura analoga.

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto
>
> ExtentText                     Name               City     State
> ----------                     ----               ----     -----
> Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA

Per apportare ulteriori modifiche ai dati nel testo estratto, la proprietà **ExtentText** acquisisce il testo non elaborato da cui è stato estratto il record. Per fornire commenti e suggerimenti su questa funzionalità o per condividere contenuto per cui risulta problematica la scrittura di esempi, inviare un messaggio di posta elettronica a <psdmfb@microsoft.com>.