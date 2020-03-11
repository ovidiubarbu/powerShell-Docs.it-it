---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Come usare la documentazione di PowerShell
ms.openlocfilehash: 7b73bc82f32e3ce1e6015822e0cc82078183931b
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279308"
---
# <a name="how-to-use-the-powershell-documentation"></a>Come usare la documentazione di PowerShell

Benvenuti nella documentazione online di PowerShell. Questo sito contiene informazioni di riferimento sui cmdlet per le versioni seguenti di PowerShell:

- PowerShell 7 (anteprima)
- PowerShell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Ricerca di articoli e selezione di una versione

Esistono due modi per cercare contenuto in Docs. Il modo più semplice consiste nell'usare la casella di filtro sotto il selettore di versione. È sufficiente immettere una parola che compare nel titolo di un articolo. Nella pagina viene visualizzato un elenco di articoli corrispondenti. È anche possibile selezionare l'opzione per eseguire la ricerca nell'intero sito da tale elenco.

Per impostazione predefinita, il sito visualizza la documentazione per la versione rilasciata più recente di PowerShell. Alcuni cmdlet funzionano in modo diverso nelle varie versioni di PowerShell. Assicurarsi di visualizzare la documentazione per la versione di PowerShell in uso.

Usare il selettore di versione nella parte superiore della pagina per selezionare la versione di PowerShell desiderata.

![Selettore di versione](media/how-to-use-docs/version-search.gif)

È possibile verificare la versione di PowerShell in uso esaminando il valore `$PSversionTable.PSVersion`. L'esempio seguente si riferisce all'output per Windows PowerShell v5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
