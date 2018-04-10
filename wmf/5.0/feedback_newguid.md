---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a>New-Guid
Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco. I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d