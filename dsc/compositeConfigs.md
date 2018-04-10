---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Annidamento delle configurazioni
ms.openlocfilehash: 9c6dbce462f7481e5714039a95ae85f85be0072e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="4b41f-103">Annidamento delle configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="4b41f-103">Nesting DSC configurations</span></span>

<span data-ttu-id="4b41f-104">Una configurazione annidata (denominata anche configurazione composita) è una configurazione che viene chiamata all'interno di un'altra configurazione come se fosse una risorsa.</span><span class="sxs-lookup"><span data-stu-id="4b41f-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="4b41f-105">Entrambe le configurazioni devono essere definite nello stesso file.</span><span class="sxs-lookup"><span data-stu-id="4b41f-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="4b41f-106">Ecco un esempio semplice:</span><span class="sxs-lookup"><span data-stu-id="4b41f-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="4b41f-107">In questo esempio, `FileConfig` accetta due parametri obbligatori, **CopyFrom** e **CopyTo**, che vengono usati come valori per le proprietà **SourcePath** e **DestinationPath** nel blocco di risorse `File`.</span><span class="sxs-lookup"><span data-stu-id="4b41f-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="4b41f-108">La configurazione `NestedConfig` chiama `FileConfig` come se fosse una risorsa.</span><span class="sxs-lookup"><span data-stu-id="4b41f-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="4b41f-109">Le proprietà nel blocco di risorse `NestedConfig` (**CopyFrom** e **CopyTo**) sono i parametri della configurazione `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="4b41f-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b41f-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4b41f-110">See Also</span></span>

- [<span data-ttu-id="4b41f-111">Risorse composite: uso di una configurazione DSC come risorsa</span><span class="sxs-lookup"><span data-stu-id="4b41f-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)