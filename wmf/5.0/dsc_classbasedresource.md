---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221851"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="15c57-102">Risorse DSC basate su classi</span><span class="sxs-lookup"><span data-stu-id="15c57-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="15c57-103">Definizione delle risorse DSC con le classi</span><span class="sxs-lookup"><span data-stu-id="15c57-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="15c57-104">In base ai commenti e ai suggerimenti ricevuti, la creazione di risorse DSC basate su classi è stata semplificata ed è di più facile comprensione.</span><span class="sxs-lookup"><span data-stu-id="15c57-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="15c57-105">Le principali differenze tra una risorsa DSC basata su classe e un provider di risorse DSC basato su cmdlet sono:</span><span class="sxs-lookup"><span data-stu-id="15c57-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="15c57-106">Non è necessario un file MOF per lo schema.</span><span class="sxs-lookup"><span data-stu-id="15c57-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="15c57-107">Non è necessaria una sottocartella **DSCResource** nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="15c57-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="15c57-108">Un file di modulo di PowerShell può contenere più classi di risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="15c57-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="15c57-109">Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="15c57-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
