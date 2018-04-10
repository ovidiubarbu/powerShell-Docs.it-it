---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a>Save-Script

Il cmdlet Save-Script consente di verificare il file di script salvandolo in una posizione specificata.

## <a name="description"></a>Description

Il cmdlet Save-Script salva lo script specificato.

## <a name="cmdlet-syntax"></a>Sintassi del cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Riferimento per la Guida online sui cmdlet

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Comandi di esempio

### <a name="example-1-save-a-script-from-a-repository"></a>Esempio 1: salvare uno script da un repository
Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Esempio 2: salvare una versione di uno script eseguendo il piping dal cmdlet Find-Script

Il primo comando trova la versione 1.5 di Fabrikam-ClientScript dal repository GalleryINT e la salva nella cartella C:\ScriptSharingDemo

Il secondo comando convalida i metadati di script salvati.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>Esempio 3: Salvare una versione provvisoria di uno script da un repository
Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```