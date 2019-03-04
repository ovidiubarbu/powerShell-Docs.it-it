---
title: Come assegnare un nome di un File CAB di Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861287"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="60c11-102">Come assegnare un nome a un file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="60c11-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="60c11-103">Questo argomento viene illustrato il formato richiesto per il file della Guida aggiornabile CAB (. File CAB).</span><span class="sxs-lookup"><span data-stu-id="60c11-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="60c11-104">Come assegnare un nome a un file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="60c11-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="60c11-105">Aggiornabile è un file CAB (. File CAB) deve avere un nome con il formato seguente.</span><span class="sxs-lookup"><span data-stu-id="60c11-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="60c11-106">Gli elementi del nome sono come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="60c11-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="60c11-107">ModuleName il valore del **nome** proprietà delle **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.</span><span class="sxs-lookup"><span data-stu-id="60c11-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="60c11-108">Il valore della **nome** proprietà del **ModuleInfo** oggetto a cui il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet restituisce.</span><span class="sxs-lookup"><span data-stu-id="60c11-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="60c11-109">ModuleGUID il valore della **GUID** chiave nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="60c11-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="60c11-110">Impostazioni cultura dell'interfaccia utente di UICulture dei file della Guida nel file CAB.</span><span class="sxs-lookup"><span data-stu-id="60c11-110">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="60c11-111">Questo valore deve corrispondere al valore di uno dei **UICulture** elementi nel file XML HelpInfo per il modulo.</span><span class="sxs-lookup"><span data-stu-id="60c11-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="60c11-112">Ad esempio, se il nome del modulo è "TestModule", il GUID del modulo è 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e le impostazioni cultura dell'interfaccia utente sono "en-US", il nome del file CAB potrebbe essere:</span><span class="sxs-lookup"><span data-stu-id="60c11-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`