---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218434"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="6333f-102">Supporto delle versioni di moduli side-by-side per le risorse DSC</span><span class="sxs-lookup"><span data-stu-id="6333f-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="6333f-103">I moduli contenenti risorse DSC possono essere installati side-by-side e le configurazioni DSC possono usare una versione specifica della risorsa installata nel sistema.</span><span class="sxs-lookup"><span data-stu-id="6333f-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="6333f-104">Per altre informazioni, vedere [Uso di risorse con più versioni](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="6333f-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="6333f-105">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="6333f-105">Known issues</span></span>

<span data-ttu-id="6333f-106">In questa versione sono presenti i seguenti problemi noti per l'installazione side-by-side:</span><span class="sxs-lookup"><span data-stu-id="6333f-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="6333f-107">Non è supportato l'uso di due diverse versioni della risorsa DSC all'interno della stessa configurazione.</span><span class="sxs-lookup"><span data-stu-id="6333f-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
