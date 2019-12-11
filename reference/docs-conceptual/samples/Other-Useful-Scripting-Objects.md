---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Altri oggetti di scripting utili
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325151"
---
# <a name="other-useful-scripting-objects"></a>Altri oggetti di scripting utili

Gli oggetti seguenti forniscono ulteriori funzionalità di scripting in Windows PowerShell ISE. Non fanno parte della gerarchia **$psISE**.

## <a name="useful-scripting-objects"></a>Oggetti di scripting utili

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Esistono alcune limitazioni sull'interazione tra Windows PowerShell ISE e le applicazioni console. Un comando o uno script di automazione che richiede l'intervento dell'utente potrebbe non funzionare nel modo giusto dalla console di Windows PowerShell. È consigliabile bloccare l'esecuzione di tali comandi o script nel riquadro dei comandi di Windows PowerShell ISE. L'oggetto **$psUnsupportedConsoleApplications** conserva un elenco di tali comandi. Se si prova a eseguire i comandi in questo elenco, viene visualizzato un messaggio che indica che non sono supportati. Lo script seguente aggiunge una voce all'elenco.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra gli argomenti della Guida e i relativi collegamenti associati nel file della Guida HTML compilato locale. Viene usato per trovare la Guida locale per un determinato argomento. È possibile aggiungere o eliminare argomenti da questo elenco. L'esempio di codice seguente mostra alcune coppie chiave-valore di esempio contenute in `$psLocalHelp`.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Lo script seguente aggiunge una voce all'elenco.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra i titoli degli argomenti della Guida e i relativi URL esterni associati. Viene usato per trovare la Guida per un determinato argomento nel Web. È possibile aggiungere o eliminare argomenti da questo elenco.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

Lo script seguente aggiunge una voce all'elenco.

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Vedere anche

[Scopo del modello a oggetti di scripting di Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
