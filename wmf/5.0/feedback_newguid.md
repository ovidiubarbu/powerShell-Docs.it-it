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
# <a name="new-guid"></a><span data-ttu-id="6a456-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="6a456-102">New-Guid</span></span>
<span data-ttu-id="6a456-103">Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco.</span><span class="sxs-lookup"><span data-stu-id="6a456-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="6a456-104">I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6a456-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="6a456-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="6a456-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="6a456-106">GUID</span><span class="sxs-lookup"><span data-stu-id="6a456-106">Guid</span></span>

----

<span data-ttu-id="6a456-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="6a456-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

