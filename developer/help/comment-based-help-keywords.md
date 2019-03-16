---
title: Parole chiave della Guida basata sui commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058080"
---
# <a name="comment-based-help-keywords"></a>Parole chiave della Guida basata sui commenti

In questo argomento elenca e descrive le parole chiave della Guida basata sui commenti.

## <a name="keywords-in-comment-based-help"></a>Parole chiave della Guida basata sui commenti

Di seguito sono valide parole chiave della Guida basata sui commenti. Essi sono elencati nell'ordine in cui vengono in genere visualizzati in un argomento della Guida in linea con l'uso previsto. Queste parole chiave possono essere visualizzati in qualsiasi ordine nella Guida basata sui commenti e non sono tra maiuscole e minuscole.

Si noti che il `.ExternalHelp` parola chiave ha la precedenza su tutte le altre parole chiave della Guida basata sui commenti. Quando `.ExternalHelp` è presente, il [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet non visualizza la Guida basata sui commenti, anche quando non riesce a trovare un file della Guida che corrisponde al valore della parola chiave.

`.Synopsis` Una breve descrizione della funzione o script. Questa parola chiave può essere utilizzata solo una volta in ogni argomento.

`.Description` Una descrizione dettagliata della funzione o script. Questa parola chiave può essere utilizzata solo una volta in ogni argomento.

`.Parameter` *\<Parametro-Name >* la descrizione di un parametro. È possibile includere un `.Parameter` parola chiave per ogni parametro della funzione o script.

Il `.Parameter` parole chiave possono essere visualizzati in qualsiasi ordine nel blocco di commento, ma l'ordine in cui i parametri vengono visualizzati nei `Param` dichiarazione di funzione o istruzione determina l'ordine in cui compaiono i parametri nell'argomento della Guida. Per modificare l'ordine dei parametri dell'argomento della Guida, modificare l'ordine dei parametri di `Param` dichiarazione di funzione o istruzione.

È anche possibile specificare una descrizione del parametro, inserendo un commento nel `Param` istruzione immediatamente prima del nome di variabile di parametro. Se si usano entrambi un `Param` commento di istruzione e una `.Parameter` parola chiave, la descrizione associata la `.Parameter` parola chiave viene usata e il `Param` istruzione commento viene ignorato.

`.Example` Un comando di esempio che usa la funzione o script, seguito facoltativamente da output di esempio e una descrizione. Ripetere questa parola chiave per ogni esempio.

`.Inputs` I tipi di Microsoft .NET Framework di oggetti che possono essere trasmesse alla funzione o script. È anche possibile includere una descrizione degli oggetti di input.

`.Outputs` Il tipo di .NET Framework degli oggetti restituiti dal cmdlet. È anche possibile includere una descrizione degli oggetti restituiti.

`.Notes` Informazioni aggiuntive sulla funzione o script.

`.Link` Il nome di un argomento correlato. Ripetere questa parola chiave per ogni argomento correlato. Questo contenuto viene visualizzato nella sezione collegamenti correlati dell'argomento della Guida.

Il `.Link` contenuto (parola chiave) può anche includere un identificatore URI (Uniform Resource) a una versione online dell'argomento della Guida stessa. La versione online viene visualizzata quando si usa il `Online` parametri di Get-Help. L'URI deve iniziare con "http" o "https".

`.Component` La tecnologia o una funzione che usa la funzione o uno script o a cui fa riferimento. Questo contenuto viene visualizzato quando il comando Get-Help include il `Component` parametri di Get-Help.

`.Role` Il ruolo utente per l'argomento della Guida. Questo contenuto viene visualizzato quando il comando Get-Help include il `Role` parametri di Get-Help.

`.Functionality` L'uso previsto della funzione. Questo contenuto viene visualizzato quando il comando Get-Help include il `Functionality` parametri di Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Effettua il reindirizzamento all'argomento della Guida per il comando specificato. È possibile reindirizzare gli utenti a qualsiasi argomento della Guida, inclusi gli argomenti della Guida per una funzione, script, i cmdlet o provider.

`.ForwardHelpCategory` `<Category>` Specifica la categoria della Guida dell'elemento in ForwardHelpTargetName. I valori validi sono Alias, Cmdlet, HelpFile, funzione, Provider, generale, domande frequenti, glossario, comando script, ExternalScript, filtro o tutti. Usare questa parola chiave per evitare conflitti quando sono presenti i comandi con lo stesso nome.

`.RemoteHelpRunspace` `<PSSession-variable>` Specifica una sessione che contiene l'argomento della Guida. Immettere una variabile che contiene una sessione PSSession. Questa parola chiave viene usata dal `Export-PSSession` cmdlet per trovare gli argomenti della Guida per i comandi esportati.

`.ExternalHelp` `<XML Help File>` Specifica il percorso e/o nome di un file della Guida basata su XML per lo script o funzione.

Il `.ExternalHelp` parola chiave indica la [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) per ottenere assistenza per la funzione o script in un file basato su XML. Il **. ExternalHelp** parola chiave è obbligatoria quando si usa un file della Guida basati su XML per una funzione o script. In caso contrario, `Get-Help` non troverà un file della Guida per la funzione o script.

Il `.ExternalHelp` parola chiave ha la precedenza su tutte le altre parole chiave della Guida basata sui commenti. Quando `.ExternalHelp` è presente, il [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet non visualizza la Guida basata sui commenti, anche quando non riesce a trovare un file della Guida che corrisponde al valore della parola chiave.

Quando la funzione venga esportata da un modulo di script, il valore di `.ExternalHelp` deve essere un nome di file senza percorso. `Get-Help` Cerca il file in una sottodirectory specifiche delle impostazioni locali della directory del modulo. Non sono previsti requisiti per il nome del file, ma una procedura consigliata consiste nell'usare il formato del nome file seguente: `<ScriptModule>.psm1-help.xml`.

Quando la funzione non è associata a un modulo, includere un percorso e nome file nel valore della **. ExternalHelp** (parola chiave). Se il percorso specificato nel file XML contiene le sottodirectory dell'interfaccia utente-impostazioni cultura specifiche, `Get-Help` ricerca in modo ricorsivo le sottodirectory per un file XML con il nome dello script o funzione in conformità con la lingua di fallback norme stabilite per Windows, proprio come si esegue per tutti gli argomenti della Guida basati su XML.

Per altre informazioni sul formato di file della Guida basata su XML della Guida cmdlet, vedere [iscritto Windows PowerShell la Guida dei Cmdlet](./writing-help-for-windows-powershell-cmdlets.md).