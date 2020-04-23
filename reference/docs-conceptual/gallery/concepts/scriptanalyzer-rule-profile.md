---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Profilo regole ScriptAnalyzer per PowerShell Gallery
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328472"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Profilo regole ScriptAnalyzer per PowerShell Gallery

Per garantire la qualità dei pacchetti pubblicati in PowerShell Gallery, eseguire le regole [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) per determinare se sono presenti eventuali violazioni negli script inviati.

L'elenco di regole è disponibile dalla [pagina di GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) relativa a ScriptAnalyzer.
Per eventuali domande sulle regole da eseguire, contattare gli amministratori di PowerShell Gallery o segnalare un problema per ScriptAnalzyer.

I risultati di ScriptAnalyzer verranno visualizzati nella pagina di ogni singolo pacchetto In PowerShell Gallery nella nuova versione. È consigliabile che i proprietari dei pacchetti si assicurino che non siano presenti errori gravi nei pacchetti pubblicati.
