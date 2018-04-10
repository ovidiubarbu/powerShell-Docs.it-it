---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="ee056-102">Informazioni dettagliate sullo stato di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="ee056-102">Detailed information about LCM state</span></span>

<span data-ttu-id="ee056-103">Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="ee056-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="ee056-104">Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="ee056-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="ee056-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="ee056-105">**Idle**</span></span>
* <span data-ttu-id="ee056-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="ee056-106">**Busy**</span></span>
* <span data-ttu-id="ee056-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="ee056-107">**PendingReboot**</span></span>
* <span data-ttu-id="ee056-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="ee056-108">**PendingConfiguration**</span></span>

<span data-ttu-id="ee056-109">È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.</span><span class="sxs-lookup"><span data-stu-id="ee056-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>