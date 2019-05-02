---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085293"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="04252-102">Parametro -Depth per Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="04252-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="04252-103">**Get-ChildItem** include ora un parametro **-Depth** utilizzabile con **-Recurse** per limitare la ricorsione:</span><span class="sxs-lookup"><span data-stu-id="04252-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="04252-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="04252-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="04252-105">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="04252-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="04252-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="04252-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="04252-107">d----- 14/04/2015 17.36 Depth0</span><span class="sxs-lookup"><span data-stu-id="04252-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="04252-108">-a---- 14/04/2015 1.19 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="04252-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="04252-109">-a---- 14/04/2015 1.19 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="04252-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="04252-110">-a---- 14/04/2015 1.19 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="04252-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="04252-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="04252-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="04252-112">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="04252-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="04252-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="04252-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="04252-114">d----- 14/04/2015 17.36 Depth0</span><span class="sxs-lookup"><span data-stu-id="04252-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="04252-115">-a---- 14/04/2015 1.19 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="04252-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="04252-116">-a---- 14/04/2015 1.19 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="04252-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="04252-117">-a---- 14/04/2015 1.19 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="04252-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="04252-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="04252-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="04252-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="04252-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="04252-120">d----- 14/04/2015 17.33 Depth1</span><span class="sxs-lookup"><span data-stu-id="04252-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
