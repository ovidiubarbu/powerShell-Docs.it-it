---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="4ccde-102">Parametro -Depth per Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4ccde-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="4ccde-103">**Get-ChildItem** include ora un parametro **-Depth** utilizzabile con **-Recurse** per limitare la ricorsione:</span><span class="sxs-lookup"><span data-stu-id="4ccde-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="4ccde-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="4ccde-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="4ccde-105">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="4ccde-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="4ccde-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="4ccde-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="4ccde-107">d----- 14/04/2015 17.36 Depth0</span><span class="sxs-lookup"><span data-stu-id="4ccde-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="4ccde-108">-a---- 14/04/2015 1.19 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="4ccde-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="4ccde-109">-a---- 14/04/2015 1.19 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="4ccde-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="4ccde-110">-a---- 14/04/2015 1.19 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="4ccde-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="4ccde-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="4ccde-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="4ccde-112">Directory: C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="4ccde-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="4ccde-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="4ccde-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="4ccde-114">d----- 14/04/2015 17.36 Depth0</span><span class="sxs-lookup"><span data-stu-id="4ccde-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="4ccde-115">-a---- 14/04/2015 1.19 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="4ccde-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="4ccde-116">-a---- 14/04/2015 1.19 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="4ccde-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="4ccde-117">-a---- 14/04/2015 1.19 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="4ccde-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="4ccde-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="4ccde-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="4ccde-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="4ccde-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="4ccde-120">d----- 14/04/2015 17.33 Depth1</span><span class="sxs-lookup"><span data-stu-id="4ccde-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

