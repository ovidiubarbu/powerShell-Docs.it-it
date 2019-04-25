---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058115"
---
# <a name="class-based-dsc-resources"></a>Risorse DSC basate su classi

## <a name="defining-dsc-resources-with-classes"></a>Definizione delle risorse DSC con le classi

In base ai commenti e ai suggerimenti ricevuti, la creazione di risorse DSC basate su classi è stata semplificata ed è di più facile comprensione.
Le principali differenze tra una risorsa DSC basata su classe e un provider di risorse DSC basato su cmdlet sono:

* Non è necessario un file MOF per lo schema.
* Non è necessaria una sottocartella **DSCResource** nella cartella del modulo.
* Un file di modulo di PowerShell può contenere più classi di risorse DSC.

Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
