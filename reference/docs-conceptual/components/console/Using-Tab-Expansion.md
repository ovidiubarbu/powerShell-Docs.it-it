---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso dell'espansione dei nomi tramite TAB
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67031018"
---
# <a name="using-tab-expansion"></a>Uso dell'espansione dei nomi tramite TAB

Le shell da riga di comando offrono spesso un modo per completare automaticamente i nomi di file o comandi lunghi, velocizzando l'immissione dei comandi e visualizzando suggerimenti. PowerShell consente di usare il tasto <kbd>TAB</kbd> per completare nomi di file e di cmdlet.

> [!NOTE]
> L'espansione tramite TAB è controllata dalla funzione interna TabExpansion o TabExpansion2. Poiché questa funzione può essere modificata o sottoposta a override, le informazioni seguenti sono da intendersi come una guida al comportamento della configurazione predefinita di PowerShell.

Per immettere automaticamente un nome di file o un percorso usando le scelte disponibili, digitare parte del nome e premere <kbd>TAB</kbd>. PowerShell espanderà automaticamente il nome usando la prima corrispondenza trovata. Premendo più volte <kbd>TAB</kbd> è possibile visualizzare in sequenza tutte le scelte disponibili.

L'espansione tramite TAB dei nomi di cmdlet è leggermente diversa. Per usare l'espansione tramite TAB per un nome di cmdlet, digitare per intero la prima parte del nome (il verbo) e il trattino che segue. È possibile immettere anche una parte più lunga del nome per ottenere una corrispondenza parziale. Ad esempio, se si digita `get-co` e si preme <kbd>TAB</kbd>, PowerShell proporrà automaticamente l'espansione al cmdlet `Get-Command`. Notare che viene cambiata anche la combinazione di maiuscole/minuscole in base al formato standard. Se si preme di nuovo <kbd>TAB</kbd>, PowerShell lo sostituisce con l'unico altro nome di cmdlet corrispondente, ossia `Get-Content`.

È possibile usare l'espansione dei nomi tramite TAB più volte sulla stessa riga. Ad esempio, è possibile usare l'espansione tramite TAB per il nome del cmdlet `Get-Content` immettendo:

```
PS> Get-Con<Tab>
```

Quando si preme <kbd>TAB</kbd>, il comando viene espanso in:

```
PS> Get-Content
```

È quindi possibile specificare parzialmente il percorso del file di log di installazione (Active Setup) e usare nuovamente la sostituzione tramite TAB:

```
PS> Get-Content c:\windows\acts<Tab>
```

Quando si preme <kbd>TAB</kbd>, il comando viene espanso in:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Uno dei limiti del processo di espansione dei nomi tramite TAB è che le pressioni di TAB vengono sempre interpretate come il tentativo di completare una parola. Se si copiano e incollano esempi di comando in una console di PowerShell, assicurarsi che l'esempio non contenga tabulazioni. In caso contrario, i risultati potrebbero essere imprevedibili e quasi certamente diversi da quelli previsti.
