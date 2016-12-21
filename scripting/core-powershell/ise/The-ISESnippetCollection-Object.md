---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Oggetto ISESnippetCollection
ms.technology: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: ad6d8ba7a68654f15566d1a74ef6a30898f21c1e
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isesnippetcollection-object"></a>Oggetto ISESnippetCollection
  L'oggetto **ISESnippetCollection** è una raccolta di oggetti **ISESnippet**. La raccolta di file associata a un oggetto **PowerShellTab** è un membro di questa classe. Un esempio è la raccolta **$psISE.CurrentPowerShellTab.Files**.

## <a name="methods"></a>Metodo

### <a name="load-filepathname-"></a>Load\( FilePathName\)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Carica un file snippets.ps1xml contenente frammenti di codice definiti dall'utente. Il modo più semplice per creare frammenti di codice consiste nell'usare il cmdlet New-IseSnippet, che li archivia automaticamente nella cartella del profilo in modo che vengano caricati ogni volta che si avvia Windows PowerShell ISE.

 **FilePathName**: la stringa specifica il percorso e il nome di un file snippets.ps1xml che contiene le definizioni dei frammenti di codice.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Vedere anche
- [ISESnippetObject](The-ISESnippetObject.md) 
- [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  
