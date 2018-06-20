---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219267"
---
# <a name="convert-string"></a>Convert-String
**Convert-String** espone funzionalità di sostituzione rapida. È sufficiente fornire esempi di "prima e dopo" per l'aspetto del testo e **Convert-String** formatta automaticamente il testo. Ecco una dimostrazione di come partire da nome e cognome e sostituirli con cognome, virgola, iniziale del nome e punto. I vantaggi sono chiari: basti pensare a quanto tempo servirebbe per ottenere lo stesso risultato con un'espressione regolare.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
