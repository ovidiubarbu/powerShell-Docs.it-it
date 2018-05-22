---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="4e5e9-102">Informazioni dettagliate sullo stato di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="4e5e9-102">Detailed information about LCM state</span></span>

<span data-ttu-id="4e5e9-103">Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="4e5e9-104">Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="4e5e9-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="4e5e9-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="4e5e9-105">**Idle**</span></span>
* <span data-ttu-id="4e5e9-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="4e5e9-106">**Busy**</span></span>
* <span data-ttu-id="4e5e9-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="4e5e9-107">**PendingReboot**</span></span>
* <span data-ttu-id="4e5e9-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="4e5e9-108">**PendingConfiguration**</span></span>

<span data-ttu-id="4e5e9-109">È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
