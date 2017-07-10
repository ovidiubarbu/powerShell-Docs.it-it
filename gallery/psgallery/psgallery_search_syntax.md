---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_search_syntax
ms.openlocfilehash: 409ae607557af760f9cec4e3c54f39e51b5fac18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="gallery-search-syntax" class="xliff"></a>
# Sintassi di ricerca di PowerShell Gallery

PowerShell Gallery offre una casella di ricerca di testo in cui è possibile usare parole, frasi ed espressioni di parole chiave per restringere i risultati della ricerca.

<a id="search-by-keywords" class="xliff"></a>
## Ricerca per parole chiave

    dsc azure sql

La funzionalità di ricerca troverà e restituirà tutti i documenti rilevanti che contengono tutte e 3 le parole chiave.

<a id="search-using-phrases-and-keywords" class="xliff"></a>
## Ricerca per frasi e parole chiave

    "azure sql" deployment

Se si immette una frase tra virgolette (""), la modalità di ricerca cambia e viene cercata la specifica frase e non le singole parole chiave.
I documenti corrispondenti in genere contengono la frase esatta "azure sql", incluse le varianti relative alle lettere maiuscole/minuscole, ad esempio "Azure SQL", e la parola 'deployment'.

<a id="filtering-on-fields" class="xliff"></a>
## Filtri relativi ai campi

È possibile cercare l'ID (oppure le varianti 'Id' o 'id') di un elemento specifico o alcuni altri campi facendolo precedere i termini della ricerca dal nome del campo.

Attualmente, i campi su cui è possibile eseguire la ricerca sono 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.

Qual è la differenza tra ID e Title? ID è il nome usato nella console. Title è ciò che viene visualizzato nella parte superiore della pagina dell'elemento nei risultati della ricerca.

<a id="examples" class="xliff"></a>
## Esempi

    ID:"PSReadline"
    id:"AzureRM.Profile"

trova gli elementi con "PSReadline" o "AzureRM.Profile" nei rispettivi campi ID.

    Id:"AzureRM.Profile"

è un altro modo per trovare gli elementi con "AzureRM.Profile" nel campo ID.

Il filtro 'Id' è una corrispondenza della sottostringa, quindi se si cerca:

    Id:"azure"
    
si ottengono risultati come 'AzureRM.Profile' e 'Azure.Storage'.

È possibile cercare anche più parole chiave in un singolo campo. Oppure combinare e associare i campi.

    id:azure tags:intellisense
    id:azure id:storage

È anche possibile eseguire ricerche di frasi:

    id:"azure.storage"


Per cercare tutti gli elementi con tag DSC.

    Tags:"DSC"

Per cercare tutti gli elementi con la funzione specificata.

    Functions:"Update-AzureRM"

Per cercare tutti gli elementi con il cmdlet specificato.
    
    Cmdlets:"Get-AzureRmEnvironment"

Per cercare tutti gli elementi con il nome della risorsa DSC specificato.

    DscResources:"xArchive"

Per cercare tutti gli elementi con PowerShellVersion specificato

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Infine, se si usa un campo non supportato, ad esempio 'commands', il campo verrà semplicemente ignorato e la ricerca verrà eseguita su tutti i campi. Quindi, la query seguente

    commands:blobs storage
    
viene interpretata esattamente come questa query:

    blobs storage

