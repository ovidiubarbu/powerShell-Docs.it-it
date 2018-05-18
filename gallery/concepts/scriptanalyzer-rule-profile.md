---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Profilo regole ScriptAnalyzer per PowerShell Gallery
ms.openlocfilehash: 22b95f0901fe95d5ad79df0e23e675ab52313fee
ms.sourcegitcommit: f8a37df92db22b9368469fb07378399b2ab90cea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="1793e-103">Profilo regole ScriptAnalyzer per PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="1793e-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="1793e-104">Per garantire la qualità degli elementi pubblicati nella raccolta di PowerShell, eseguire le regole [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) per determinare se sono presenti eventuali violazioni negli script inviati.</span><span class="sxs-lookup"><span data-stu-id="1793e-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="1793e-105">L'elenco di regole è disponibile dalla [pagina di GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) relativa a ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="1793e-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="1793e-106">Per eventuali domande sulle regole da eseguire, contattare gli amministratori della raccolta di PowerShell o segnalare un problema per ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="1793e-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="1793e-107">I risultati di ScriptAnalyzer verranno visualizzati in ogni pagina degli elementi della raccolta nella nuova versione.</span><span class="sxs-lookup"><span data-stu-id="1793e-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="1793e-108">È consigliabile che i proprietari degli elementi si assicurino che non siano presenti errori gravi negli elementi pubblicati.</span><span class="sxs-lookup"><span data-stu-id="1793e-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
