---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a>Convert-String
**Convert-String** espone funzionalità di sostituzione rapida. È sufficiente fornire esempi di "prima e dopo" per l'aspetto del testo e **Convert-String** formatta automaticamente il testo. Ecco una dimostrazione di come partire da nome e cognome e sostituirli con cognome, virgola, iniziale del nome e punto. I vantaggi sono chiari: basti pensare a quanto tempo servirebbe per ottenere lo stesso risultato con un'espressione regolare.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```