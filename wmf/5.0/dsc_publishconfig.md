---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Recapitare un documento di configurazione senza applicarlo

Il cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copia un file MOF di configurazione in un nodo di destinazione, ma non applica la configurazione.
Questa configurazione viene applicata durante il passaggio di controllo della coerenza successivo o quando si esegue il cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).