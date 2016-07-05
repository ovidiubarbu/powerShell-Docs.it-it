---
title: "Appendice 1 - Alias per la compatibilità"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 38a6cb1b0402825b307652e6747ea65baafd1d8b

---

# Appendice 1 - Alias per la compatibilità
Windows PowerShell include diversi alias di transizione che consentono agli utenti di UNIX e di Cmd di usare i nomi di comandi familiari in Windows PowerShell. Gli alias più comuni sono indicati nella tabella seguente, insieme al comando di Windows PowerShell corrispondente all'alias e all'alias di Windows PowerShell standard, se esistente.

È possibile trovare il comando di Windows PowerShell a cui punta qualsiasi alias dall'interno di Windows PowerShell tramite il cmdlet Get\-Alias. Ad esempio, digitare **get\-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comando CMD|Comando UNIX|Comando PS|Alias PS|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get\-ChildItem**|**gci**|
|**cls**|**clear**|**Clear\-Host** (funzione)|N\/D|
|**del, erase, rmdir**|**rm**|**Remove\-Item**|**ri**|
|**copy**|**cp**|**Copy\-Item**|**ci**|
|**move**|**mv**|**Move\-Item**|**mi**|
|**rename**|**mv**|**Rename\-Item**|**rni**|
|**tipo**|**cat**|**Get\-Content**|**gc**|
|**cd**|**cd**|**Set\-Location**|**sl**|
|**md**|**mkdir**|**New\-Item**|**ni**|
|N\/D|**pushd**|**Push\-Location**|N\/D|
|N\/D|**popd**|**Pop\-Location**|N\/D|




<!--HONumber=Jun16_HO4-->


