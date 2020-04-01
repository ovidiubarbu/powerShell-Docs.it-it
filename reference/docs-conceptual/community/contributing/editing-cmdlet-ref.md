---
title: Modifica degli articoli di riferimento
description: Questo articolo illustra i requisiti specifici per la modifica delle informazioni di riferimento sui cmdlet e degli argomenti About nella documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500966"
---
# <a name="editing-reference-articles"></a>Modifica degli articoli di riferimento

Gli articoli di riferimento sui cmdlet hanno una struttura specifica. Questa struttura è definita da [PlatyPS][].
PlatyPS genera la Guida del cmdlet per i moduli di PowerShell in Markdown. Dopo la modifica dei file markdown, PlatyPS viene usato per creare i file della Guida MAML usati dal cmdlet `Get-Help`.

PlatyPS ha uno schema hardcoded per le informazioni di riferimento del cmdlet scritte nel codice. Il documento [platyPS.schema.md][] tenta di descrivere questa struttura. Le violazioni dello schema causano errori di compilazione che è necessario correggere prima che il contributo sia accettato.

## <a name="general-guidelines"></a>Linee guida generali

- Non rimuovere le strutture di intestazione. PlatyPS accetta uno specifico set di intestazioni.
- Le intestazioni **Input type** e **Output type** devono avere un tipo. Se il cmdlet non accetta input o restituisce un valore, usare il valore `None`.
- I blocchi di codice delimitati sono consentiti solo nella sezione [Examples](#structuring-examples).
- Gli intervalli di codice incorporati possono essere usati in qualsiasi paragrafo.

## <a name="formatting-about_-files"></a>Formattazione dei file About_

I file `About_*` vengono ora elaborati da [Pandoc][], anziché da PlatyPS. I file `About_*` sono formattati in modo da ottenere la massima compatibilità con tutte le versioni di PowerShell e con gli strumenti di pubblicazione.

Linee guida di base per la formattazione:

- Limitare le righe a 80 caratteri
- Il limite per i blocchi di codice e le tabelle è di 76 caratteri perché Pandoc imposta un rientro di quattro spazi durante la conversione in testo normale
- Le tabelle devono rientrare nei 76 caratteri
  - Mandare a capo manualmente il contenuto delle celle su più righe
  - Usare i caratteri `|` di apertura e chiusura in ogni riga
  - Vedere un esempio funzionante in [about_Comparison_Operators][about-example]
- Uso dei caratteri speciali Pandoc `\`,`$` e `<`
  - All'interno di un'intestazione, questi caratteri devono essere preceduti dal carattere di escape `\` o racchiusi tra apici inversi (`` ` ``)
  - All'interno di un paragrafo, questi caratteri devono essere inseriti in intervalli di codice. Ad esempio:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a>Formato per gli esempi

Nello schema PlatyPS l'intestazione **EXAMPLES** è un'intestazione H2 e ogni esempio è un'intestazione H3.

All'interno di un esempio, lo schema non consente la separazione dei blocchi di codice tramite paragrafi. Lo schema supportato è:

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Numerare ogni esempio e aggiungere un breve titolo.

Ad esempio:

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>Esempio 1: Ottenere cmdlet, funzioni e alias

Questo comando ottiene i cmdlet, le funzioni e gli alias di PowerShell installati nel computer.

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>Esempio 2: Ottenere i comandi nella sessione corrente

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>Passaggi successivi

[Elenco di controllo editoriale](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
