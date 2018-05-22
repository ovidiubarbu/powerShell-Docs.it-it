---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Profilo regole ScriptAnalyzer per PowerShell Gallery
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="b5c43-103">Profilo regole ScriptAnalyzer per PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="b5c43-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="b5c43-104">Per garantire la qualità degli elementi pubblicati nella raccolta di PowerShell, eseguire le regole [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) per determinare se sono presenti eventuali violazioni negli script inviati.</span><span class="sxs-lookup"><span data-stu-id="b5c43-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="b5c43-105">L'elenco di regole è disponibile dalla [pagina di GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) relativa a ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="b5c43-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="b5c43-106">Per eventuali domande sulle regole da eseguire, contattare gli amministratori della raccolta di PowerShell o segnalare un problema per ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="b5c43-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="b5c43-107">I risultati di ScriptAnalyzer verranno visualizzati in ogni pagina degli elementi della raccolta nella nuova versione.</span><span class="sxs-lookup"><span data-stu-id="b5c43-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="b5c43-108">È consigliabile che i proprietari degli elementi si assicurino che non siano presenti errori gravi negli elementi pubblicati.</span><span class="sxs-lookup"><span data-stu-id="b5c43-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
