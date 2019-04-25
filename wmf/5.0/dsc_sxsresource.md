---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057928"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Supporto delle versioni di moduli side-by-side per le risorse DSC

I moduli contenenti risorse DSC possono essere installati side-by-side e le configurazioni DSC possono usare una versione specifica della risorsa installata nel sistema.

Per altre informazioni, vedere [Uso di risorse con più versioni](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemi noti

In questa versione sono presenti i seguenti problemi noti per l'installazione side-by-side:

-   Non è supportato l'uso di due diverse versioni della risorsa DSC all'interno della stessa configurazione.
