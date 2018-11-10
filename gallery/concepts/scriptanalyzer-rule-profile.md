---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Profilo regole ScriptAnalyzer per PowerShell Gallery
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002497"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="3ff75-103">Profilo regole ScriptAnalyzer per PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="3ff75-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="3ff75-104">Per garantire la qualità dei pacchetti pubblicati in PowerShell Gallery, eseguire le regole [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) per determinare se sono presenti eventuali violazioni negli script inviati.</span><span class="sxs-lookup"><span data-stu-id="3ff75-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="3ff75-105">L'elenco di regole è disponibile dalla [pagina di GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) relativa a ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="3ff75-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="3ff75-106">Per eventuali domande sulle regole da eseguire, contattare gli amministratori della raccolta di PowerShell o segnalare un problema per ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="3ff75-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="3ff75-107">I risultati di ScriptAnalyzer verranno visualizzati nella pagina di ogni singolo pacchetto In PowerShell Gallery nella nuova versione.</span><span class="sxs-lookup"><span data-stu-id="3ff75-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="3ff75-108">È consigliabile che i proprietari dei pacchetti si assicurino che non siano presenti errori gravi nei pacchetti pubblicati.</span><span class="sxs-lookup"><span data-stu-id="3ff75-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
