---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058404"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="fff16-102">Non è necessario che le frequenze per RefreshMode e ConfigurationMode siano multipli l'una dell'altra</span><span class="sxs-lookup"><span data-stu-id="fff16-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="fff16-103">Nella versione precedente di DSC, Gestione configurazione locale gestisce `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` come multipli reciproci.</span><span class="sxs-lookup"><span data-stu-id="fff16-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="fff16-104">In WMF 5.0 RTM, queste proprietà vengono elaborate in modo indipendente.</span><span class="sxs-lookup"><span data-stu-id="fff16-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="fff16-105">Per altre informazioni, vedere [Configurazione di Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="fff16-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
