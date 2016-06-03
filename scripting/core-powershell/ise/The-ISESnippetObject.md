---
title:  ISESnippetObject
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
---

# ISESnippetObject
  Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet. I membri della raccolta **$psISE.CurrentPowerShellTab.Snippets** sono tutti esempi di oggetti **ISESnippet**. Il modo più semplice per creare un frammento di codice consiste nell'usare il cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

## Proprietà

###  <a name="DisplayName"></a> Autore
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <a name="Action"></a> CodeFragment
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <a name="Shortcut"></a> Collegamento
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## Vedere anche
 [Oggetto ISESnippetCollection](The-ISESnippetCollection-Object.md) 
 [The Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) (Modello a oggetti di scripting di Windows PowerShell ISE) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


