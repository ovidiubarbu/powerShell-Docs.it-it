---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetObject
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736965"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet. I membri della raccolta `$psISE.CurrentPowerShellTab.Snippets` sono tutti esempi di oggetti **ISESnippet**. Il modo più semplice per creare un frammento di codice è l'uso del cmdlet [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md).

## <a name="properties"></a>Proprietà

### <a name="author"></a>Autore

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Tasto di scelta rapida

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
