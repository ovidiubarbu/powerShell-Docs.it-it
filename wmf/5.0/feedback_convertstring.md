---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="convert-string" class="xliff"></a>
# Convert-String
**Convert-String** espone funzionalità di sostituzione rapida. È sufficiente fornire esempi di "prima e dopo" per l'aspetto del testo e **Convert-String** formatta automaticamente il testo. Ecco una dimostrazione di come partire da nome e cognome e sostituirli con cognome, virgola, iniziale del nome e punto. I vantaggi sono chiari: basti pensare a quanto tempo servirebbe per ottenere lo stesso risultato con un'espressione regolare.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

