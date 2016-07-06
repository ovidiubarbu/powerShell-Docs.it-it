---
title: Oggetto ISESnippetCollection
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 1d899709f3a0caa2c957fc8b84f00eeb597a47fa

---

# Oggetto ISESnippetCollection
  L'oggetto **ISESnippetCollection** è una raccolta di oggetti **ISESnippet**. La raccolta di file associata a un oggetto **PowerShellTab** è un membro di questa classe. Un esempio è la raccolta **$psISE.CurrentPowerShellTab.Files**.

## Metodo

### Load\( FilePathName \)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Carica un file snippets.ps1xml contenente frammenti di codice definiti dall'utente. Il modo più semplice per creare frammenti di codice consiste nell'usare il cmdlet New\-IseSnippet, che li archivia automaticamente nella cartella del profilo in modo che vengano caricati ogni volta che si avvia Windows PowerShell ISE.

 **FilePathName** - Stringa Il percorso e nome di un file snippets.ps1xml che contiene le definizioni del frammento di codice.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## Vedere anche
 [ISESnippetObject](The-ISESnippetObject.md) 
 [Modello a oggetti di Scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Jun16_HO4-->


