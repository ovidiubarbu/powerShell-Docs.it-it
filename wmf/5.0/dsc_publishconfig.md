---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Recapitare un documento di configurazione senza applicarlo

Il cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copia un file MOF di configurazione in un nodo di destinazione, ma non applica la configurazione.
Questa configurazione viene applicata durante il passaggio di controllo della coerenza successivo o quando si esegue il cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).
