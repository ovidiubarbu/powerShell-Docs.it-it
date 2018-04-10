---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Appendice 1 Alias per la compatibilità
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
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