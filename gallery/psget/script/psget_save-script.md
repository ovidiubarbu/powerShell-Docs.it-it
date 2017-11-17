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
# <a name="save-script"></a><span data-ttu-id="bcf6b-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="bcf6b-103">Save-Script</span></span>

<span data-ttu-id="bcf6b-104">Il cmdlet Save-Script consente di verificare il file di script salvandolo in una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="bcf6b-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="bcf6b-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bcf6b-105">Description</span></span>

<span data-ttu-id="bcf6b-106">Il cmdlet Save-Script salva lo script specificato.</span><span class="sxs-lookup"><span data-stu-id="bcf6b-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="bcf6b-107">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="bcf6b-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="bcf6b-108">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="bcf6b-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="bcf6b-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="bcf6b-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="bcf6b-110">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="bcf6b-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="bcf6b-111">Esempio 1: salvare uno script da un repository</span><span class="sxs-lookup"><span data-stu-id="bcf6b-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="bcf6b-112">Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="bcf6b-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="bcf6b-113">Esempio 2: salvare una versione di uno script eseguendo il piping dal cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="bcf6b-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="bcf6b-114">Il primo comando trova la versione 1.5 di Fabrikam-ClientScript dal repository GalleryINT e la salva nella cartella C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="bcf6b-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="bcf6b-115">Il secondo comando convalida i metadati di script salvati.</span><span class="sxs-lookup"><span data-stu-id="bcf6b-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

