---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="new-guid" class="xliff"></a>
# New-Guid
Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco. I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d

