---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="save-script" class="xliff"></a>
# Save-Script

Il cmdlet Save-Script consente di verificare il file di script salvandolo in una posizione specificata.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Save-Script salva lo script specificato.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

<a id="example-commands" class="xliff"></a>
## Comandi di esempio

<a id="example-1-save-a-script-from-a-repository" class="xliff"></a>
### Esempio 1: salvare uno script da un repository
Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

<a id="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet" class="xliff"></a>
### Esempio 2: salvare una versione di uno script eseguendo il piping dal cmdlet Find-Script

Il primo comando trova la versione 1.5 di Fabrikam-ClientScript dal repository GalleryINT e la salva nella cartella C:\ScriptSharingDemo

Il secondo comando convalida i metadati di script salvati.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

