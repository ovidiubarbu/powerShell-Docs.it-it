---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISESnippetCollection
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736046"
---
# <a name="the-isesnippetcollection-object"></a>Oggetto ISESnippetCollection

L'oggetto **ISESnippetCollection** è una raccolta di oggetti **ISESnippet**. La raccolta di file associata a un oggetto **PowerShellTab** è un membro di questa classe. Un esempio è la raccolta `$psISE.CurrentPowerShellTab.Files`.

## <a name="methods"></a>Metodi

### <a name="load-filepathname-"></a>Load\( FilePathName\)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Carica un file `.snippets.ps1xml` contenente frammenti di codice definiti dall'utente. Il modo più semplice per creare frammenti di codice è l'uso del cmdlet `New-IseSnippet`. In questo modo, i frammenti vengono automaticamente archiviati nella cartella del proprio profilo e caricati ogni volta che si avvia Windows PowerShell ISE.

**FilePathName**: la stringa specifica il percorso e il nome di un file snippets.ps1xml che contiene le definizioni dei frammenti di codice.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Vedere anche

- [ISESnippetObject](The-ISESnippetObject.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
