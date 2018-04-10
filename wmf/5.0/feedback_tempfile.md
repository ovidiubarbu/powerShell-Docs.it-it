---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="ab1a2-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="ab1a2-102">New-TemporaryFile</span></span>
<span data-ttu-id="ab1a2-103">A volte, negli script è necessario creare un file temporaneo.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="ab1a2-104">È possibile farlo facilmente con il cmdlet **New-TemporaryFile**:</span><span class="sxs-lookup"><span data-stu-id="ab1a2-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="ab1a2-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="ab1a2-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="ab1a2-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="ab1a2-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="ab1a2-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="ab1a2-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>