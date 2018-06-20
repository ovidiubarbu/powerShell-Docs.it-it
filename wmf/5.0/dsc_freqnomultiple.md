---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218383"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="edcee-102">Non è necessario che le frequenze per RefreshMode e ConfigurationMode siano multipli l'una dell'altra</span><span class="sxs-lookup"><span data-stu-id="edcee-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="edcee-103">Nella versione precedente di DSC, Gestione configurazione locale gestisce `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` come multipli reciproci.</span><span class="sxs-lookup"><span data-stu-id="edcee-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="edcee-104">In WMF 5.0 RTM, queste proprietà vengono elaborate in modo indipendente.</span><span class="sxs-lookup"><span data-stu-id="edcee-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="edcee-105">Per altre informazioni, vedere [Configurazione di Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="edcee-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
