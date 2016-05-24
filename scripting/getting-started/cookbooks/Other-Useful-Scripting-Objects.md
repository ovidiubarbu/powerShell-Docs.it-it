---
title: Altri oggetti di scripting utili
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
---
# Altri oggetti di scripting utili
  Gli oggetti seguenti forniscono ulteriori funzionalità di scripting in Windows PowerShell ISE. Non fanno parte della gerarchia **$psISE**.

## Oggetti di scripting utili

### $psUnsupportedConsoleApplications
 Esistono alcune limitazioni sull'interazione tra Windows PowerShell ISE e le applicazioni console. Un comando o uno script di automazione che richiede l'intervento dell'utente potrebbe non funzionare nel modo giusto dalla console di Windows PowerShell. È consigliabile bloccare l'esecuzione di tali comandi o script nel riquadro dei comandi di Windows PowerShell ISE. L'oggetto **$psUnsupportedConsoleApplications** conserva un elenco di tali comandi. Se si prova a eseguire i comandi in questo elenco, viene visualizzato un messaggio che indica che non sono supportati. Lo script seguente aggiunge una voce all'elenco.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### $psLocalHelp
 Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra gli argomenti della Guida e i relativi collegamenti associati nel file della Guida HTML compilato locale. Viene usato per trovare la Guida locale per un determinato argomento. È possibile aggiungere o eliminare argomenti da questo elenco. L'esempio di codice seguente mostra alcune coppie chiave-valore contenute in **$psLocalHelp**..

```
# See the local help map
$psLocalHelp |Format-List

```

### Output di esempio

|||
|-|-|
|Chiave: Add-Computer|Valore: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Chiave: Add-Content|Valore: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 Lo script seguente aggiunge una voce all'elenco.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### $psOnlineHelp
 Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra i titoli degli argomenti della Guida e i relativi URL esterni associati. Viene usato per trovare la Guida per un determinato argomento nel Web. È possibile aggiungere o eliminare argomenti da questo elenco.

```
$psOnlineHelp |format-list

```

### Output di esempio

|||
|-|-|
|Chiave: Add-Computer|Valore: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Chiave: Add-Content|Valore: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Lo script seguente aggiunge una voce all'elenco.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## Vedere anche
 [Modello a oggetti di scripting di Windows PowerShell ISE](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


