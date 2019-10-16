---
title: Scrittura della Guida per gli script e le funzioni di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367720"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Scrittura della Guida per le funzioni e gli script di PowerShell

Gli script e le funzioni di PowerShell devono essere documentati in modo completo ogni volta che vengono condivisi con altri utenti.
Il cmdlet `Get-Help` Visualizza gli argomenti della Guida per gli script e le funzioni nello stesso formato in cui viene visualizzata la guida per i cmdlet di e tutti i parametri `Get-Help` funzionano sugli argomenti della Guida relativi agli script e alle funzioni.

Gli script di PowerShell possono includere un argomento della guida sugli script e gli argomenti della guida su ogni funzione nello script.
Le funzioni condivise indipendentemente dagli script possono includere argomenti della guida.

Questo documento illustra il formato e la posizione corretta degli argomenti della guida e suggerisce le linee guida per il contenuto.

## <a name="types-of-script-and-function-help"></a>Tipi di script e guida per le funzioni

### <a name="comment-based-help"></a>Guida basata su Commenti
L'argomento della guida che descrive uno script o una funzione può essere implementato come un set di commenti nello script o nella funzione.
Quando si scrive la guida basata su commenti per uno script e per le funzioni in uno script, prestare particolare attenzione alle regole per l'inserimento della Guida basata su commenti.
La selezione host determina se il cmdlet `Get-Help` associa l'argomento della Guida allo script o a una funzione.
Per ulteriori informazioni sulla scrittura degli argomenti della Guida basati su commenti, vedere [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Guida per i comandi basati su XML
L'argomento della guida che descrive uno script o una funzione può essere implementato in un file XML che utilizza lo schema della guida del comando.
Per associare lo script o la funzione al file XML, usare la parola chiave del commento `ExternalHelp` seguita dal percorso e dal nome del file XML.

Quando la parola chiave del commento `ExternalHelp` è presente, ha la precedenza sulla guida basata su commenti, anche quando `Get-Help` non è in grado di trovare un file della guida che corrisponda al valore della parola chiave `ExternalHelp`.

### <a name="online-help"></a>Guida in linea
È possibile pubblicare gli argomenti della guida su Internet e quindi indirizzare `Get-Help` per aprire gli argomenti.
Per ulteriori informazioni sulla scrittura degli argomenti della Guida basati su commenti, vedere Supporto per la [Guida online](../module/supporting-online-help.md).

Non esiste un metodo stabilito per la scrittura di argomenti concettuali ("about") per gli script e le funzioni.
È tuttavia possibile pubblicare argomenti concettuali in Internet elencare gli argomenti e i rispettivi URL nella sezione collegamenti correlati di un argomento della guida del comando.

## <a name="content-considerations-for-script-and-function-help"></a>Considerazioni sul contenuto per la Guida di script e funzioni

- Se si sta scrivendo un argomento della guida molto breve con solo alcune delle sezioni della guida sui comandi disponibili, assicurarsi di includere descrizioni chiare dei parametri dello script o della funzione. Includere anche uno o due comandi di esempio nella sezione degli esempi, anche se si decide di omettere le descrizioni di esempio.

- In tutte le descrizioni, fare riferimento al comando come uno script o una funzione. Queste informazioni consentono all'utente di comprendere e gestire il comando.

  La descrizione dettagliata seguente indica, ad esempio, che il comando New-Topic è uno script. In questo modo si ricorda agli utenti che devono specificare il percorso e il nome completo durante l'esecuzione.

  > "Lo script New-Topic crea un argomento concettuale vuoto per ogni nome di argomento nel file di input..."

  La descrizione dettagliata seguente indica che `Disable-PSRemoting` è una funzione. Queste informazioni sono particolarmente utili per gli utenti quando la sessione include più comandi con lo stesso nome, alcuni dei quali potrebbero essere nascosti da un comando con precedenza maggiore.

  > La funzione `Disable-PSRemoting` Disabilita tutte le configurazioni di sessione nel computer locale...

- In un argomento della Guida di script, spiegare come usare lo script nel suo complesso. Se si scrivono anche gli argomenti della Guida per le funzioni nello script, menzionare le funzioni nell'argomento della Guida per gli script e includere i riferimenti agli argomenti della Guida per le funzioni nella sezione collegamenti correlati dell'argomento della Guida per lo script. Viceversa, quando una funzione fa parte di uno script, spiegare nell'argomento della guida della funzione il ruolo che la funzione svolge nello script e il modo in cui può essere utilizzata in modo indipendente. Quindi, elencare l'argomento della Guida per gli script nella sezione collegamenti correlati dell'argomento della guida della funzione.

- Quando si scrivono esempi per un argomento della Guida di script, assicurarsi di includere il percorso del file di script nel comando di esempio. Ciò ricorda agli utenti che devono specificare il percorso in modo esplicito, anche quando lo script si trova nella directory corrente.

- In un argomento della guida della funzione ricordare agli utenti che la funzione esiste solo nella sessione corrente e, per usarla in altre sessioni, è necessario aggiungerla o aggiungerla a un profilo di PowerShell.

- `Get-Help` Visualizza l'argomento della Guida relativo a uno script o a una funzione solo quando il file di script e i file degli argomenti della guida vengono salvati nei percorsi corretti. Non è pertanto utile includere le istruzioni per l'installazione di PowerShell o il salvataggio o l'installazione dello script o della funzione in un argomento della Guida relativo a uno script o una funzione. Al contrario, includere le istruzioni di installazione nel documento utilizzato per distribuire lo script o la funzione.

## <a name="see-also"></a>Vedere anche

[Scrittura degli argomenti della Guida basati su Commenti](./writing-comment-based-help-topics.md)
