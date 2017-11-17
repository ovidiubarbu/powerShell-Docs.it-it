---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: b178f198c9643fb39a6499d7e957cfd0d848c52d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="cb1c8-103">Profilo regole ScriptAnalyzer per raccolta</span><span class="sxs-lookup"><span data-stu-id="cb1c8-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="cb1c8-104">Per garantire la qualità degli elementi pubblicati nella raccolta di PowerShell, eseguire le regole [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) per determinare se sono presenti eventuali violazioni negli script inviati.</span><span class="sxs-lookup"><span data-stu-id="cb1c8-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="cb1c8-105">L'elenco di regole è disponibile dalla [pagina di GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) relativa a ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="cb1c8-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="cb1c8-106">Per eventuali domande sulle regole da eseguire, contattare gli amministratori della raccolta di PowerShell o segnalare un problema per ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="cb1c8-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="cb1c8-107">I risultati di ScriptAnalyzer verranno visualizzati in ogni pagina degli elementi della raccolta nella nuova versione.</span><span class="sxs-lookup"><span data-stu-id="cb1c8-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="cb1c8-108">È consigliabile che i proprietari degli elementi si assicurino che non siano presenti errori gravi negli elementi pubblicati.</span><span class="sxs-lookup"><span data-stu-id="cb1c8-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>

