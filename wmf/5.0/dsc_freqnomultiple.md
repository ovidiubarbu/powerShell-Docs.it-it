---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Non è necessario che le frequenze per RefreshMode e ConfigurationMode siano multipli l'una dell'altra

Nella versione precedente di DSC, Gestione configurazione locale gestisce `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` come multipli reciproci. In WMF 5.0 RTM, queste proprietà vengono elaborate in modo indipendente.

Per altre informazioni, vedere [Configurazione di Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig).