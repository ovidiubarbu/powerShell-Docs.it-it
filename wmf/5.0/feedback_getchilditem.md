---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="701bd-102">Parametro -Depth per Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="701bd-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="701bd-103">**Get-ChildItem** include ora un parametro **-Depth** utilizzabile con **-Recurse** per limitare la ricorsione:</span><span class="sxs-lookup"><span data-stu-id="701bd-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="701bd-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="701bd-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="701bd-105">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="701bd-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="701bd-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="701bd-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="701bd-107">d----- 14/04/2015 17.36 Depth0</span><span class="sxs-lookup"><span data-stu-id="701bd-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="701bd-108">-a---- 14/04/2015 1.19 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="701bd-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="701bd-109">-a---- 14/04/2015 1.19 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="701bd-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="701bd-110">-a---- 14/04/2015 1.19 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="701bd-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="701bd-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="701bd-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="701bd-112">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="701bd-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="701bd-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="701bd-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="701bd-114">d----- 14/04/2015 17.36 Depth0</span><span class="sxs-lookup"><span data-stu-id="701bd-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="701bd-115">-a---- 14/04/2015 1.19 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="701bd-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="701bd-116">-a---- 14/04/2015 1.19 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="701bd-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="701bd-117">-a---- 14/04/2015 1.19 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="701bd-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="701bd-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="701bd-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="701bd-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="701bd-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="701bd-120">d----- 14/04/2015 17.33 Depth1</span><span class="sxs-lookup"><span data-stu-id="701bd-120">d----- 4/14/2015 5:33 PM Depth1</span></span>