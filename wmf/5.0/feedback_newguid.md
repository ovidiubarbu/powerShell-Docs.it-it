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
# <a name="new-guid"></a><span data-ttu-id="9de41-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="9de41-102">New-Guid</span></span>
<span data-ttu-id="9de41-103">Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco.</span><span class="sxs-lookup"><span data-stu-id="9de41-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="9de41-104">I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9de41-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="9de41-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="9de41-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="9de41-106">GUID</span><span class="sxs-lookup"><span data-stu-id="9de41-106">Guid</span></span>

----

<span data-ttu-id="9de41-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="9de41-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>