---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Sintassi di ricerca di PowerShell Gallery
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742857"
---
# <a name="gallery-search-syntax"></a>Sintassi di ricerca di PowerShell Gallery

È possibile cercare la PowerShell Gallery usando il [sito web della raccolta di PowerShell](https://www.powershellgallery.com/).
Sito web di PowerShell Gallery offre searchbox un testo in cui è possibile usare parole, frasi ed espressioni di parole chiave per restringere i risultati della ricerca.

## <a name="search-by-keywords"></a>Ricerca per parole chiave

    dsc azure sql

Ricerca tenta di trovare documenti rilevanti che contengono tutte le parole 3 chiave e restituire documenti corrispondenti.

## <a name="search-using-phrases-and-keywords"></a>Ricerca per frasi e parole chiave

    "azure sql" deployment

Se si immette una frase tra virgolette (""), la modalità di ricerca cambia e viene cercata la specifica frase e non le singole parole chiave.
I documenti corrispondenti in genere contengono la frase esatta "azure sql", incluse le varianti relative alle lettere maiuscole/minuscole, ad esempio "Azure SQL", e la parola 'deployment'.

## <a name="filtering-on-fields"></a>Filtri relativi ai campi

È possibile cercare l'ID (oppure le varianti 'Id' o 'id') di un pacchetto specifico o alcuni altri campi anteponendo il nome del campo ai termini della ricerca.

Attualmente, i campi su cui è possibile eseguire la ricerca sono 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.

Qual è la differenza tra ID e Title? ID è il nome usato nella console. Title è ciò che viene visualizzato nella parte superiore della pagina del pacchetto nei risultati della ricerca.

## <a name="examples"></a>Esempi

    ID:PSReadline
    
Trova tutti i pacchetti con un ID contenente "PSReadline".

    Id:"AzureRM.Profile"

è un altro modo per trovare i pacchetti con "AzureRM.Profile" nel campo ID.

Il filtro 'Id' è una corrispondenza della sottostringa, quindi se si cerca:

    Id:"azure"

In questo modo i risultati che includono azurerm. Profile ' e 'Storage'.

È possibile cercare anche più parole chiave in un singolo campo. 

    id:azure tags:intellisense

Ed è possibile eseguire ricerche di frasi usando le virgolette doppie:

    id:"azure.storage"

Per cercare tutti i pacchetti con tag DSC.

    Tags:DSC

Per cercare tutti i pacchetti con la funzione specificata.

    Functions:Get-TreeSize

Per cercare tutti i pacchetti con il cmdlet specificato.

    Cmdlets:Get-AzureRmEnvironment

Per cercare tutti i pacchetti con il nome di risorsa DSC specificato.

    DscResources:xArchive

Per cercare tutti i pacchetti con il valore PowerShellVersion specificato

    PowerShellVersion:2.0

Infine, se si usa un campo non supportato, ad esempio 'commands', il campo verrà semplicemente ignorato e la ricerca verrà eseguita su tutti i campi. Quindi, la query seguente

    commands:blobs storage

viene interpretata esattamente come questa query:

    blobs storage
