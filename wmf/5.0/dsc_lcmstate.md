---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085797"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="834a7-102">Informazioni dettagliate sullo stato di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="834a7-102">Detailed information about LCM state</span></span>

<span data-ttu-id="834a7-103">Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="834a7-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="834a7-104">Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="834a7-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="834a7-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="834a7-105">**Idle**</span></span>
* <span data-ttu-id="834a7-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="834a7-106">**Busy**</span></span>
* <span data-ttu-id="834a7-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="834a7-107">**PendingReboot**</span></span>
* <span data-ttu-id="834a7-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="834a7-108">**PendingConfiguration**</span></span>

<span data-ttu-id="834a7-109">È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.</span><span class="sxs-lookup"><span data-stu-id="834a7-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
