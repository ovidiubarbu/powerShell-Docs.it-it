---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Supporto delle versioni di moduli side-by-side per le risorse DSC

I moduli contenenti risorse DSC possono essere installati side-by-side e le configurazioni DSC possono usare una versione specifica della risorsa installata nel sistema.

Per altre informazioni, vedere [Uso di risorse con più versioni](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemi noti

In questa versione sono presenti i seguenti problemi noti per l'installazione side-by-side:

-   Non è supportato l'uso di due diverse versioni della risorsa DSC all'interno della stessa configurazione.
