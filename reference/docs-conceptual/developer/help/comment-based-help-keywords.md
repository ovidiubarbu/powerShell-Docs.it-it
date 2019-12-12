---
title: Parole chiave della guida basate su Commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361360"
---
# <a name="comment-based-help-keywords"></a>Parole chiave della Guida basata sui commenti

In questo argomento vengono elencate e descritte le parole chiave nella Guida basata su commenti.

## <a name="keywords-in-comment-based-help"></a>Parole chiave nella Guida basata su Commenti

Di seguito sono riportate le parole chiave della guida basate su Commenti valide. Sono elencate nell'ordine in cui vengono in genere visualizzate in un argomento della guida insieme all'utilizzo previsto. Queste parole chiave possono essere visualizzate in qualsiasi ordine nella Guida basata su commenti e non fanno distinzione tra maiuscole e minuscole.

Si noti che la parola chiave `.ExternalHelp` ha la precedenza su tutte le altre parole chiave della guida basate su commenti. Quando `.ExternalHelp` è presente, il cmdlet [Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) non Visualizza la guida basata sui commenti, anche quando non è in grado di trovare un file della guida che corrisponda al valore della parola chiave.

`.Synopsis` una breve descrizione della funzione o dello script. Questa parola chiave può essere utilizzata solo una volta in ogni argomento.

`.Description` una descrizione dettagliata della funzione o dello script. Questa parola chiave può essere utilizzata solo una volta in ogni argomento.

`.Parameter` *\<nome-parametro >* la descrizione di un parametro. È possibile includere una parola chiave `.Parameter` per ogni parametro nella funzione o nello script.

Le parole chiave `.Parameter` possono essere visualizzate in qualsiasi ordine nel blocco di commento, ma l'ordine in cui i parametri vengono visualizzati nell'istruzione `Param` o nella dichiarazione di funzione determina l'ordine in cui i parametri vengono visualizzati nell'argomento della guida. Per modificare l'ordine dei parametri nell'argomento della guida, modificare l'ordine dei parametri nell'istruzione `Param` o nella dichiarazione di funzione.

È anche possibile specificare una descrizione del parametro inserendo un commento nell'istruzione `Param` immediatamente prima del nome della variabile del parametro. Se si usano sia un commento di istruzione `Param` che una parola chiave `.Parameter`, viene usata la descrizione associata alla parola chiave `.Parameter` e il commento dell'istruzione `Param` viene ignorato.

`.Example` un comando di esempio che utilizza la funzione o lo script, seguito facoltativamente dall'output di esempio e da una descrizione. Ripetere questa parola chiave per ogni esempio.

`.Inputs` i tipi di Microsoft .NET Framework di oggetti che possono essere inviati tramite pipe alla funzione o allo script. È anche possibile includere una descrizione degli oggetti di input.

`.Outputs` il tipo di .NET Framework degli oggetti restituiti dal cmdlet. È anche possibile includere una descrizione degli oggetti restituiti.

`.Notes` informazioni aggiuntive sulla funzione o sullo script.

`.Link` il nome di un argomento correlato. Ripetere questa parola chiave per ogni argomento correlato. Questo contenuto viene visualizzato nella sezione collegamenti correlati dell'argomento della guida.

Il contenuto della parola chiave `.Link` può includere anche un Uniform Resource Identifier (URI) a una versione online dello stesso argomento della guida. La versione online si apre quando si usa il parametro `Online` di Get-Help. L'URI deve iniziare con "http" o "https".

`.Component` la tecnologia o la funzionalità utilizzata dalla funzione o dallo script oppure a cui è correlata. Questo contenuto viene visualizzato quando il comando Get-Help include il parametro `Component` di Get-Help.

`.Role` il ruolo utente per l'argomento della guida. Questo contenuto viene visualizzato quando il comando Get-Help include il parametro `Role` di Get-Help.

`.Functionality` l'uso previsto della funzione. Questo contenuto viene visualizzato quando il comando Get-Help include il parametro `Functionality` di Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` reindirizza all'argomento della Guida per il comando specificato. È possibile reindirizzare gli utenti a qualsiasi argomento della guida, inclusi gli argomenti della Guida per una funzione, uno script, un cmdlet o un provider.

`.ForwardHelpCategory` `<Category>` specifica la categoria della Guida dell'elemento in ForwardHelpTargetName. I valori validi sono alias, cmdlet, fileguida, funzione, provider, generale, domande frequenti, glossario, ScriptCommand, ExternalScript, filtro o tutti. Usare questa parola chiave per evitare conflitti quando sono presenti comandi con lo stesso nome.

`.RemoteHelpRunspace` `<PSSession-variable>` specifica una sessione che contiene l'argomento della guida. Immettere una variabile che contiene una sessione PSSession. Questa parola chiave viene utilizzata dal cmdlet `Export-PSSession` per trovare gli argomenti della Guida per i comandi esportati.

`.ExternalHelp` `<XML Help File>` specifica il percorso e/o il nome di un file della guida basato su XML per la funzione o lo script.

La parola chiave `.ExternalHelp` indica al cmdlet [Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) di ottenere la guida per lo script o la funzione in un file basato su XML. Oggetto **.** La parola chiave ExternalHelp è obbligatoria quando si usa un file della guida basato su XML per uno script o una funzione. Senza di esso, `Get-Help` non troverà un file della Guida per la funzione o lo script.

La parola chiave `.ExternalHelp` ha la precedenza su tutte le altre parole chiave della guida basate su commenti. Quando `.ExternalHelp` è presente, il cmdlet [Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) non Visualizza la guida basata sui commenti, anche quando non è in grado di trovare un file della guida che corrisponda al valore della parola chiave.

Quando la funzione viene esportata da un modulo di script, il valore di `.ExternalHelp` deve essere un nome di file senza percorso. `Get-Help` Cerca il file in una sottodirectory specifica delle impostazioni locali della directory del modulo. Non sono previsti requisiti per il nome file, ma è consigliabile usare il formato di nome file seguente: `<ScriptModule>.psm1-help.xml`.

Quando la funzione non è associata a un modulo, includere un percorso e un nome file nel valore di **.** Parola chiave ExternalHelp. Se il percorso specificato del file XML contiene sottodirectory specifiche delle impostazioni cultura dell'interfaccia utente, `Get-Help` Cerca in modo ricorsivo le sottodirectory di un file XML con il nome dello script o della funzione in base agli standard di fallback della lingua stabiliti per Windows, proprio come per tutti gli argomenti della Guida basati su XML.

Per ulteriori informazioni sul formato di file della guida basato su XML per i cmdlet, vedere [scrittura della Guida dei cmdlet di Windows PowerShell](./writing-help-for-windows-powershell-cmdlets.md).