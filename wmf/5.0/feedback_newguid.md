---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085327"
---
# <a name="new-guid"></a><span data-ttu-id="e835b-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="e835b-102">New-Guid</span></span>
<span data-ttu-id="e835b-103">Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco.</span><span class="sxs-lookup"><span data-stu-id="e835b-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="e835b-104">I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e835b-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="e835b-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="e835b-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="e835b-106">GUID</span><span class="sxs-lookup"><span data-stu-id="e835b-106">Guid</span></span>

----

<span data-ttu-id="e835b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="e835b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
