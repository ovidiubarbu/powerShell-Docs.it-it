---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a>ISESnippetObject
  Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet. I membri della raccolta **$psISE.CurrentPowerShellTab.Snippets** sono tutti esempi di oggetti **ISESnippet**. Il modo più semplice per creare un frammento di codice consiste nell'usare il cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).

## <a name="properties"></a>Proprietà

### <a name="author"></a>Autore
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>Collegamento
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

 Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Vedere anche
- [Oggetto ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
