---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086672"
---
# <a name="the-isesnippetcollection-object"></a>Oggetto ISESnippetCollection

L'oggetto **ISESnippetCollection** è una raccolta di oggetti **ISESnippet**. La raccolta di file associata a un oggetto **PowerShellTab** è un membro di questa classe. Un esempio è la raccolta **$psISE.CurrentPowerShellTab.Files**.

## <a name="methods"></a>Metodi

### <a name="load-filepathname-"></a>Load\( FilePathName\)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Carica un file snippets.ps1xml contenente frammenti di codice definiti dall'utente. Il modo più semplice per creare frammenti di codice consiste nell'usare il cmdlet New-IseSnippet, che li archivia automaticamente nella cartella del profilo in modo che vengano caricati ogni volta che si avvia Windows PowerShell ISE.

**FilePathName**: la stringa specifica il percorso e il nome di un file snippets.ps1xml che contiene le definizioni dei frammenti di codice.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Vedere anche

- [ISESnippetObject](The-ISESnippetObject.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)