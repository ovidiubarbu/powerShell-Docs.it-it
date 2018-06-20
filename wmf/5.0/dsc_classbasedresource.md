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
# <a name="class-based-dsc-resources"></a>Risorse DSC basate su classi

## <a name="defining-dsc-resources-with-classes"></a>Definizione delle risorse DSC con le classi

In base ai commenti e ai suggerimenti ricevuti, la creazione di risorse DSC basate su classi è stata semplificata ed è di più facile comprensione.
Le principali differenze tra una risorsa DSC basata su classe e un provider di risorse DSC basato su cmdlet sono:

* Non è necessario un file MOF per lo schema.
* Non è necessaria una sottocartella **DSCResource** nella cartella del modulo.
* Un file di modulo di PowerShell può contenere più classi di risorse DSC.

Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
