---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Annidamento delle configurazioni
ms.openlocfilehash: 89badda86707a129909b1c3cc3f79afa0b5f5df6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-dsc-configurations"></a>Annidamento delle configurazioni DSC

Una configurazione annidata (denominata anche configurazione composita) è una configurazione che viene chiamata all'interno di un'altra configurazione come se fosse una risorsa.
Entrambe le configurazioni devono essere definite nello stesso file.

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

In questo esempio, `FileConfig` accetta due parametri obbligatori, **CopyFrom** e **CopyTo**, che vengono usati come valori per le proprietà **SourcePath** e **DestinationPath** nel blocco di risorse `File`. La configurazione `NestedConfig` chiama `FileConfig` come se fosse una risorsa.
Le proprietà nel blocco di risorse `NestedConfig` (**CopyFrom** e **CopyTo**) sono i parametri della configurazione `FileConfig`.

## <a name="see-also"></a>Vedere anche

- [Risorse composite: uso di una configurazione DSC come risorsa](authoringResourceComposite.md)

