---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678136"
---
# <a name="new-guid"></a><span data-ttu-id="ecc0b-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="ecc0b-102">New-Guid</span></span>
<span data-ttu-id="ecc0b-103">Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco.</span><span class="sxs-lookup"><span data-stu-id="ecc0b-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="ecc0b-104">I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ecc0b-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="ecc0b-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="ecc0b-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="ecc0b-106">GUID</span><span class="sxs-lookup"><span data-stu-id="ecc0b-106">Guid</span></span>

----

<span data-ttu-id="ecc0b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="ecc0b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
