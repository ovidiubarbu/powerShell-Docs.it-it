---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085814"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Recapitare un documento di configurazione senza applicarlo

Il cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copia un file MOF di configurazione in un nodo di destinazione, ma non applica la configurazione.
Questa configurazione viene applicata durante il passaggio di controllo della coerenza successivo o quando si esegue il cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).
