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
ms.openlocfilehash: fc715f9ba2a1dc61d2549d5370371fe2b29fa063
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="appendix-1---compatibility-aliases"></a>Appendice 1 - Alias per la compatibilità
Windows PowerShell include diversi alias di transizione che consentono agli utenti di UNIX e di Cmd di usare i nomi di comandi familiari in Windows PowerShell. Gli alias più comuni sono indicati nella tabella seguente, insieme al comando di Windows PowerShell corrispondente all'alias e all'alias di Windows PowerShell standard, se esistente.

È possibile trovare il comando di Windows PowerShell a cui punta qualsiasi alias dall'interno di Windows PowerShell tramite il cmdlet Get-Alias. Ad esempio, digitare **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comando CMD|Comando UNIX|Comando PS|Alias PS|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (funzione)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|

