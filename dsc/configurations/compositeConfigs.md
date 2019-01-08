---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Annidamento delle configurazioni
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401224"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="b4100-103">Annidamento delle configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="b4100-103">Nesting DSC configurations</span></span>

<span data-ttu-id="b4100-104">Una configurazione annidata (denominata anche configurazione composita) è una configurazione che viene chiamata all'interno di un'altra configurazione come se fosse una risorsa.</span><span class="sxs-lookup"><span data-stu-id="b4100-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="b4100-105">Entrambe le configurazioni devono essere definite nello stesso file.</span><span class="sxs-lookup"><span data-stu-id="b4100-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="b4100-106">Ecco un esempio semplice:</span><span class="sxs-lookup"><span data-stu-id="b4100-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="b4100-107">In questo esempio, `FileConfig` accetta due parametri obbligatori, **CopyFrom** e **CopyTo**, che vengono usati come valori per le proprietà **SourcePath** e **DestinationPath** nel blocco di risorse `File`.</span><span class="sxs-lookup"><span data-stu-id="b4100-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="b4100-108">La configurazione `NestedConfig` chiama `FileConfig` come se fosse una risorsa.</span><span class="sxs-lookup"><span data-stu-id="b4100-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="b4100-109">Le proprietà nel blocco di risorse `NestedConfig` (**CopyFrom** e **CopyTo**) sono i parametri della configurazione `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="b4100-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4100-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b4100-110">See Also</span></span>

- [<span data-ttu-id="b4100-111">Risorse composite: uso di una configurazione DSC come risorsa</span><span class="sxs-lookup"><span data-stu-id="b4100-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)