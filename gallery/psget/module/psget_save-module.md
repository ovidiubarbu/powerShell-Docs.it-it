---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Module
ms.openlocfilehash: 296c5c5ffc6f1e12da0162237e562b13b3679110
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="save-module"></a><span data-ttu-id="e3c93-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e3c93-103">Save-Module</span></span>

<span data-ttu-id="e3c93-104">Consente di salvare un modulo in locale senza installarlo.</span><span class="sxs-lookup"><span data-stu-id="e3c93-104">Saves a module locally without installing it.</span></span>

## <a name="description"></a><span data-ttu-id="e3c93-105">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e3c93-105">Description</span></span>

<span data-ttu-id="e3c93-106">Il cmdlet Save-Module consente di salvare un modulo in locale dal repository specificato per l'ispezione.</span><span class="sxs-lookup"><span data-stu-id="e3c93-106">The Save-Module cmdlet saves a module locally from the specified repository for inspection.</span></span> <span data-ttu-id="e3c93-107">Il modulo non viene installato.</span><span class="sxs-lookup"><span data-stu-id="e3c93-107">The module is not installed.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="e3c93-108">Sintassi del cmdlet</span><span class="sxs-lookup"><span data-stu-id="e3c93-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="e3c93-109">Riferimento per la Guida online sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="e3c93-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="e3c93-110">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e3c93-110">Save-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=531351)

## <a name="example-commands"></a><span data-ttu-id="e3c93-111">Comandi di esempio</span><span class="sxs-lookup"><span data-stu-id="e3c93-111">Example commands</span></span>

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath

```

