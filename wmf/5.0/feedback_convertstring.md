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
# <a name="convert-string"></a><span data-ttu-id="5fadf-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="5fadf-102">Convert-String</span></span>
<span data-ttu-id="5fadf-103">**Convert-String** espone funzionalità di sostituzione rapida.</span><span class="sxs-lookup"><span data-stu-id="5fadf-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="5fadf-104">È sufficiente fornire esempi di "prima e dopo" per l'aspetto del testo e **Convert-String** formatta automaticamente il testo.</span><span class="sxs-lookup"><span data-stu-id="5fadf-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="5fadf-105">Ecco una dimostrazione di come partire da nome e cognome e sostituirli con cognome, virgola, iniziale del nome e punto.</span><span class="sxs-lookup"><span data-stu-id="5fadf-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="5fadf-106">I vantaggi sono chiari: basti pensare a quanto tempo servirebbe per ottenere lo stesso risultato con un'espressione regolare.</span><span class="sxs-lookup"><span data-stu-id="5fadf-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

