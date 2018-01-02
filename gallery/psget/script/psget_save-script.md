---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="save-script"></a><span data-ttu-id="d0f70-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="d0f70-103">Save-Script</span></span>

<span data-ttu-id="d0f70-104">Il cmdlet Save-Script consente di verificare il file di script salvandolo in una posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="d0f70-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="d0f70-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d0f70-105">Description</span></span>

<span data-ttu-id="d0f70-106">Il cmdlet Save-Script salva lo script specificato.</span><span class="sxs-lookup"><span data-stu-id="d0f70-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d0f70-107">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0f70-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d0f70-108">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0f70-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="d0f70-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="d0f70-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="d0f70-110">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="d0f70-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="d0f70-111">Esempio 1: salvare uno script da un repository</span><span class="sxs-lookup"><span data-stu-id="d0f70-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="d0f70-112">Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="d0f70-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="d0f70-113">Esempio 2: salvare una versione di uno script eseguendo il piping dal cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="d0f70-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="d0f70-114">Il primo comando trova la versione 1.5 di Fabrikam-ClientScript dal repository GalleryINT e la salva nella cartella C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="d0f70-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="d0f70-115">Il secondo comando convalida i metadati di script salvati.</span><span class="sxs-lookup"><span data-stu-id="d0f70-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="d0f70-116">Esempio 3: Salvare una versione provvisoria di uno script da un repository</span><span class="sxs-lookup"><span data-stu-id="d0f70-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="d0f70-117">Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="d0f70-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

