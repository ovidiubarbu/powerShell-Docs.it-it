---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a><span data-ttu-id="a1497-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="a1497-102">New-Guid</span></span>
<span data-ttu-id="a1497-103">Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco.</span><span class="sxs-lookup"><span data-stu-id="a1497-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="a1497-104">I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a1497-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="a1497-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="a1497-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="a1497-106">GUID</span><span class="sxs-lookup"><span data-stu-id="a1497-106">Guid</span></span>

----

<span data-ttu-id="a1497-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="a1497-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
