---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Risorse DSC basate su classi

## <a name="defining-dsc-resources-with-classes"></a>Definizione delle risorse DSC con le classi

In base ai commenti e ai suggerimenti ricevuti, la creazione di risorse DSC basate su classi è stata semplificata ed è di più facile comprensione.
Le principali differenze tra una risorsa DSC basata su classe e un provider di risorse DSC basato su cmdlet sono:

* Non è necessario un file MOF per lo schema.
* Non è necessaria una sottocartella **DSCResource** nella cartella del modulo.
* Un file di modulo di PowerShell può contenere più classi di risorse DSC.

Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).