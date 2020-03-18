---
title: Elenco di controllo editoriale
description: Elenco riassuntivo delle regole per la modifica della documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060336"
---
# <a name="editors-checklist"></a>Elenco di controllo del redattore

Di seguito è riportato un riepilogo delle regole da applicare quando si scrivono nuovi articoli o si aggiornano quelli esistenti. Per spiegazioni dettagliate ed esempi di queste regole, vedere gli altri articoli della Guida per i collaboratori.

## <a name="metadata"></a>Metadati

- `ms.date`: il formato deve essere **MM/DD/YYYY**
  - Cambiare la data in presenza di un aggiornamento reale o significativo
    - Riorganizzazione dell'articolo
    - Correzione di errori reali
    - Aggiunta di nuove informazioni
  - Non cambiare la data se l'aggiornamento non è significativo
    - Correzione di errori di digitazione e formattazione
- `title`: stringa univoca di 43-59 caratteri, spazi inclusi
  - Non includere l'identificatore del sito (viene generato automaticamente)
  - Usare la maiuscola a inizio frase, ovvero usare la maiuscola solo per la prima parola ed eventuali nomi propri
- `description`: 115-145 caratteri, spazi inclusi; questo sunto viene visualizzato nei risultati della ricerca

## <a name="formatting"></a>Formattazione

- Elementi di sintassi apice inverso visualizzati, incorporati, all'interno di un paragrafo
  - Nomi di cmdlet `Verb-Noun`
  - Variabile `$counter`
  - Esempi sintattici `Verb-Noun -Parameter`
  - Percorsi di file `C:\Program Files\PowerShell`, `/usr/bin/pwsh`
  - URL non selezionabili nel documento
- Usare il grassetto per nomi di proprietà, valori di parametri, nomi di parametri, nomi di classi, nomi di moduli, nomi di entità, nomi di oggetti o tipi
  - Il grassetto viene usato per il markup semantico, non per dare enfasi
  - Grassetto: usare gli asterischi `**`
- Corsivo: usare il carattere di sottolineatura `_`
  - Usato solo per dare enfasi, non per il markup semantico
- Interruzioni di riga a 100 colonne (o a 80 per **about_Topics**)
- Nessuna tabulazione, usare solo spazi
- Niente spazi finali nelle righe

### <a name="headers"></a>Headers

- H1 per prima: una sola intestazione H1 per articolo
- Usare solo [intestazioni ATX](https://github.github.com/gfm/#atx-headings)
- Usare la maiuscola a inizio frase per tutte le intestazioni
- Non saltare i livelli: non usare H3 senza H2
- Profondità massima di H3 o H4
- Riga vuota prima e dopo
- PlatyPS applica intestazioni specifiche nel proprio schema; non aggiungere o rimuovere intestazioni

### <a name="code-blocks"></a>Blocchi di codice

- Riga vuota prima e dopo
- Usare blocchi di codice con tag: **powershell**, **Output** o altro ID di linguaggio appropriato
- Blocco senza tag: blocchi di sintassi o altre shell
- Inserire **Output** in un blocco di codice separato, ad eccezione di esempi semplici in cui non si vuole che il lettore usi il pulsante **Copy**
- Vedere l'elenco dei [linguaggi supportati](/contribute/code-in-docs#supported-languages)

### <a name="lists"></a>Elenchi

- Rientri impostati correttamente
- Riga vuota prima del primo elemento e dopo l'ultimo elemento
- Punto elenco: usare il segno meno (`-`) e non l'asterisco (`*`), troppo facile da confondere con l'enfasi
- Per gli elenchi numerati, tutti i numeri sono "1."

## <a name="terminology"></a>Terminologia

- PowerShell, Windows PowerShell e PowerShell Core
- Vedere [Terminologia dei prodotti](powershell-style-guide.md#product-terminology)

## <a name="cmdlet-reference-examples"></a>Esempi di riferimento per i cmdlet

- Deve essere presente almeno un esempio nelle informazioni di riferimento sui cmdlet
- Gli esempi devono riportare il codice sufficiente per illustrare l'utilizzo
- Sintassi di Powershell
  - Usare i nomi completi di cmdlet e parametri, non gli alias
  - Usare lo splatting per i parametri quando la riga di comando diventa troppo lunga
  - Evitare di usare apici inversi come caratteri di continuazione di riga; usare solo quando necessario
- Rimuovere o semplificare il prompt di PowerShell (`PS>`) tranne nei casi in cui è necessario per l'esempio
- L'esempio di riferimento per il cmdlet deve seguire lo schema PlatyPS seguente

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- Non inserire paragrafi tra i blocchi di codice. Tutto il contenuto descrittivo deve essere posizionato prima o dopo i blocchi di codice.

## <a name="linking-to-other-documents"></a>Collegamento ad altri documenti

- Collegamento all'esterno del set di documenti o tra le informazioni di riferimento sui cmdlet e concettuali
  - Usare URL relativi per il collegamento a docs.microsoft.com (rimuovere `https://docs.microsoft.com/en-us`)
  - Non includere le impostazioni locali negli URL nelle proprietà Microsoft (ad esempio, rimuovere `/en-us` dall'URL)
  - Tutti gli URL che puntano a siti Web esterni devono usare HTTPS, a meno che ciò non sia valido per il sito di destinazione
- All'interno del set di documenti
  - Collegare al percorso del file (ad esempio, `../folder/file.md`)
  - Tutti i percorsi di file usano caratteri barra (`/`)
- I collegamenti alle immagini devono avere un testo alternativo univoco
