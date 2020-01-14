---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Annidamento delle configurazioni
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75417860"
---
# <a name="nesting-dsc-configurations"></a>Annidamento delle configurazioni DSC

Una configurazione annidata, denominata anche configurazione composita, è una configurazione che viene chiamata all'interno di un'altra configurazione come se fosse una risorsa. Entrambe le configurazioni devono essere definite nello stesso file.

Ecco un esempio semplice:

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

In questo esempio, `FileConfig` accetta due parametri obbligatori, **CopyFrom** e **CopyTo**, che vengono usati come valori per le proprietà **SourcePath** e **DestinationPath** nel blocco di risorse `File`. La configurazione `NestedConfig` chiama `FileConfig` come se fosse una risorsa. Le proprietà nel blocco di risorse `NestedConfig` (**CopyFrom** e **CopyTo**) sono i parametri della configurazione `FileConfig`.

DSC attualmente non supporta la nidificazione delle configurazioni all'interno delle configurazioni annidate. È possibile solo annidare una configurazione a un livello di profondità.

## <a name="see-also"></a>Vedere anche

- [Risorse composite: uso di una configurazione DSC come risorsa](../resources/authoringResourceComposite.md)