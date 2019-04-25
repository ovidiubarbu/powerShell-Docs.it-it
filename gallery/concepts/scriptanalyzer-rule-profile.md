---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Profilo regole ScriptAnalyzer per PowerShell Gallery
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084590"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="d933b-103">Profilo regole ScriptAnalyzer per PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d933b-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="d933b-104">Per garantire la qualità dei pacchetti pubblicati in PowerShell Gallery, eseguire le regole [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) per determinare se sono presenti eventuali violazioni negli script inviati.</span><span class="sxs-lookup"><span data-stu-id="d933b-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="d933b-105">L'elenco di regole è disponibile dalla [pagina di GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) relativa a ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="d933b-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="d933b-106">Per eventuali domande sulle regole da eseguire, contattare gli amministratori di PowerShell Gallery o segnalare un problema per ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="d933b-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="d933b-107">I risultati di ScriptAnalyzer verranno visualizzati nella pagina di ogni singolo pacchetto In PowerShell Gallery nella nuova versione.</span><span class="sxs-lookup"><span data-stu-id="d933b-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="d933b-108">È consigliabile che i proprietari dei pacchetti si assicurino che non siano presenti errori gravi nei pacchetti pubblicati.</span><span class="sxs-lookup"><span data-stu-id="d933b-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
