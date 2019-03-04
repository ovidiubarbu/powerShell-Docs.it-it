---
title: Scrittura della Guida per gli script di PowerShell e le funzioni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857477"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Guida alla scrittura per le funzioni e script di PowerShell

Funzioni e script di PowerShell devono essere completamente documentate ogni volta che vengono condivise con altri utenti.
Il `Get-Help` cmdlet consente di visualizzare gli argomenti della Guida di script e la funzione nello stesso formato quando visualizza la Guida per cmdlet e tutti i `Get-Help` parametri usati in script e la funzione gli argomenti della Guida.

Gli script di PowerShell possono includere un argomento della Guida relative allo script e gli argomenti della Guida su ogni funzioni nello script.
Le funzioni che vengono condivisi indipendentemente da script possono includere i propri argomenti della Guida.

Questo documento viene illustrato il formato e il posizionamento corretto degli argomenti della Guida, pertanto si consiglia di linee guida per il contenuto.

## <a name="types-of-script-and-function-help"></a>Tipi di Script e della Guida (funzione)

### <a name="comment-based-help"></a>Guida basata sui commenti
L'argomento della Guida che descrive una funzione o script può essere implementato come una serie di commenti nello script o funzione.
Durante la scrittura della Guida basata su commenti per uno script e per le funzioni in uno script, prestare particolare attenzione alle regole per posizionare la Guida basata sui commenti.
La selezione host determina se il `Get-Help` cmdlet associa l'argomento della Guida con lo script o una funzione.
Per altre informazioni su come scrivere argomenti della Guida basata sui commenti, vedere [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Guida dei comandi basato su XML
L'argomento della Guida che descrive una funzione o script può essere implementata in un file XML che utilizza lo schema di Guida in linea di comando.
Per associare lo script o funzione con il file XML, usare il `ExternalHelp` commento (parola chiave) seguito dal percorso e nome del file XML.

Quando il `ExternalHelp` commentare la parola chiave è presente, ha la precedenza su Guida basata sui commenti, anche quando `Get-Help` non è stato trovato un file della Guida che corrisponde al valore della `ExternalHelp` (parola chiave).

### <a name="online-help"></a>Guida
È possibile inviare argomenti della Guida su Internet e quindi indirizzare `Get-Help` per visualizzare la Guida.
Per altre informazioni su come scrivere argomenti della Guida basata sui commenti, vedere [supporto della Guida Online](../module/supporting-online-help.md).

Non vi è alcun metodo di consolidata per la scrittura concettuale ("About"), gli argomenti per gli script e funzioni.
Tuttavia, è possibile pubblicare argomenti concettuali nell'elenco Internet gli argomenti e i relativi URL nella sezione collegamenti correlati di un argomento della Guida in linea di comando.

## <a name="content-considerations-for-script-and-function-help"></a>Considerazioni sul contenuto per lo Script e la funzione Guida in linea

- Se si sta scrivendo un argomento della Guida molto breve con solo alcune delle sezioni della Guida dei comandi disponibili, assicurarsi di includere deselezionare le descrizioni dei parametri di script o una funzione. Includere anche uno o due comandi di esempio nella sezione esempi, anche se si decide di omettere le descrizioni di esempio.

- In tutte le descrizioni, fare riferimento al comando come uno script o funzione. Queste informazioni consentono all'utente di comprendere e gestire il comando.

  Ad esempio, la descrizione dettagliata seguente indica che il comando New-argomento è uno script. Questo ricorda agli utenti a cui hanno bisogno per specificare il percorso e il nome completo quando viene eseguito.

  > "Lo script New-argomento crea un argomento concettuale vuoto per ogni nome di argomento nel file di input..."

  La descrizione dettagliata seguente dichiara che `Disable-PSRemoting` è una funzione. Queste informazioni sono particolarmente utili agli utenti quando la sessione include più comandi con lo stesso nome, alcuni dei quali può essere nascosto da un comando con precedenza maggiore.

  > Il `Disable-PSRemoting` funzione disabilita tutte le configurazioni di sessione nel computer locale...

- In un argomento della Guida di script, viene illustrato come usare lo script nel suo complesso. Se si siano scrivendo anche gli argomenti della Guida per le funzioni nello script, menzionare le funzioni nell'argomento della Guida di script e includere i riferimenti agli argomenti della Guida funzione nella sezione collegamenti correlati dell'argomento della Guida dello script. Al contrario, quando una funzione è parte di uno script, viene illustrato nell'argomento della Guida funzione il ruolo che svolge la funzione in script e come può essere usato in modo indipendente. Quindi, elencare l'argomento della Guida di script nella sezione collegamenti correlati dell'argomento della Guida funzione.

- Durante la scrittura di esempi per un argomento della Guida di script, assicurarsi di includere il percorso del file di script nell'esempio di comando. Questo ricorda agli utenti che devono specificare il percorso in modo esplicito, anche quando lo script si trova nella directory corrente.

- In un argomento della Guida funzione, gli utenti sapranno che la funzione esiste solo nella sessione corrente e, per utilizzarla in altre sessioni, è necessario aggiungerla o aggiungere un profilo di PowerShell.

- `Get-Help` Visualizza l'argomento della Guida per uno script o funzione solo quando il file di script e i file degli argomenti della Guida vengono salvati nelle posizioni corrette. Non è pertanto utile includere le istruzioni per l'installazione di PowerShell, o il salvataggio o l'installazione di script o funzione in un argomento della Guida funzione o script. Includono invece le istruzioni di installazione nel documento che si userà per distribuire lo script o funzione.

## <a name="see-also"></a>Vedere anche

 [Scrivere argomenti della Guida basati su XML per gli script e funzioni](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Scrivere argomenti della Guida basati su XML per i comandi](./writing-xml-based-help-topics-for-commands.md)

 [Scrivere argomenti della Guida basata sui commenti](./writing-comment-based-help-topics.md)
