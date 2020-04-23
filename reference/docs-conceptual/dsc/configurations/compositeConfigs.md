---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Annidamento delle configurazioni
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75417860"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="6ede9-103">Annidamento delle configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="6ede9-103">Nesting DSC configurations</span></span>

<span data-ttu-id="6ede9-104">Una configurazione annidata, denominata anche configurazione composita, è una configurazione che viene chiamata all'interno di un'altra configurazione come se fosse una risorsa.</span><span class="sxs-lookup"><span data-stu-id="6ede9-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="6ede9-105">Entrambe le configurazioni devono essere definite nello stesso file.</span><span class="sxs-lookup"><span data-stu-id="6ede9-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="6ede9-106">Ecco un esempio semplice:</span><span class="sxs-lookup"><span data-stu-id="6ede9-106">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
    {
        SourcePath = $CopyFrom
        DestinationPath = $CopyTo
        Ensure = 'Present'
    }
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="6ede9-107">In questo esempio, `FileConfig` accetta due parametri obbligatori, **CopyFrom** e **CopyTo**, che vengono usati come valori per le proprietà **SourcePath** e **DestinationPath** nel blocco di risorse `File`.</span><span class="sxs-lookup"><span data-stu-id="6ede9-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="6ede9-108">La configurazione `NestedConfig` chiama `FileConfig` come se fosse una risorsa.</span><span class="sxs-lookup"><span data-stu-id="6ede9-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="6ede9-109">Le proprietà nel blocco di risorse `NestedConfig` (**CopyFrom** e **CopyTo**) sono i parametri della configurazione `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="6ede9-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="6ede9-110">DSC attualmente non supporta la nidificazione delle configurazioni all'interno delle configurazioni annidate.</span><span class="sxs-lookup"><span data-stu-id="6ede9-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="6ede9-111">È possibile solo annidare una configurazione a un livello di profondità.</span><span class="sxs-lookup"><span data-stu-id="6ede9-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ede9-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6ede9-112">See Also</span></span>

- [<span data-ttu-id="6ede9-113">Risorse composite: uso di una configurazione DSC come risorsa</span><span class="sxs-lookup"><span data-stu-id="6ede9-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)