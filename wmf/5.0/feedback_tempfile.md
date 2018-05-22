---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="6b412-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6b412-102">New-TemporaryFile</span></span>
<span data-ttu-id="6b412-103">A volte, negli script è necessario creare un file temporaneo.</span><span class="sxs-lookup"><span data-stu-id="6b412-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="6b412-104">È possibile farlo facilmente con il cmdlet **New-TemporaryFile**:</span><span class="sxs-lookup"><span data-stu-id="6b412-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="6b412-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6b412-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="6b412-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="6b412-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="6b412-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="6b412-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
