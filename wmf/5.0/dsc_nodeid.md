---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188286"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="68742-102">Separazione degli ID per nodi e configurazioni</span><span class="sxs-lookup"><span data-stu-id="68742-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="68742-103">Panoramica</span><span class="sxs-lookup"><span data-stu-id="68742-103">Overview</span></span>

<span data-ttu-id="68742-104">Per garantire un'esperienza più flessibile e semplificata durante l'uso di DSC in modalità Pull, in questa versione sono state aggiunte numerose funzionalità.</span><span class="sxs-lookup"><span data-stu-id="68742-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="68742-105">Queste funzionalità sono progettate in modo da offrire la flessibilità necessaria per configurare e distribuire le configurazioni su più nodi, offrendo allo stesso tempo la possibilità di tenere traccia dello stato e di creare report di informazioni per ogni nodo singolarmente.</span><span class="sxs-lookup"><span data-stu-id="68742-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="68742-106">Queste funzionalità sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="68742-106">These features are as follows:</span></span>

* <span data-ttu-id="68742-107">Un nome di configurazione che identifica la configurazione per un computer.</span><span class="sxs-lookup"><span data-stu-id="68742-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="68742-108">Questo nome può essere condiviso da più nodi di destinazione</span><span class="sxs-lookup"><span data-stu-id="68742-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="68742-109">Un ID di agente che identifica in modo univoco un singolo nodo</span><span class="sxs-lookup"><span data-stu-id="68742-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="68742-110">Un passaggio di registrazione che si verifica solo la prima volta che un nodo di destinazione si connette a un server di pull</span><span class="sxs-lookup"><span data-stu-id="68742-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="68742-111">**Nota:** queste caratteristiche e funzionalità sono state aggiunte e non sostituiscono i concetti e le funzionalità esistenti relativi al pull.</span><span class="sxs-lookup"><span data-stu-id="68742-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="68742-112">È possibile usare queste nuove funzionalità o quelle meno recenti con il nuovo server di pull incluso in questa versione.</span><span class="sxs-lookup"><span data-stu-id="68742-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="68742-113">Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).</span><span class="sxs-lookup"><span data-stu-id="68742-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
