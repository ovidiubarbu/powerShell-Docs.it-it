---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="d58c8-102">Informazioni dettagliate sullo stato di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="d58c8-102">Detailed information about LCM state</span></span>

<span data-ttu-id="d58c8-103">Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="d58c8-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="d58c8-104">Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="d58c8-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="d58c8-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="d58c8-105">**Idle**</span></span>
* <span data-ttu-id="d58c8-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="d58c8-106">**Busy**</span></span>
* <span data-ttu-id="d58c8-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="d58c8-107">**PendingReboot**</span></span>
* <span data-ttu-id="d58c8-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="d58c8-108">**PendingConfiguration**</span></span>

<span data-ttu-id="d58c8-109">È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.</span><span class="sxs-lookup"><span data-stu-id="d58c8-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

