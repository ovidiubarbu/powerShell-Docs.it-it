---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ordinamento degli oggetti
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401188"
---
# <a name="sorting-objects"></a><span data-ttu-id="3d86b-103">Ordinamento degli oggetti</span><span class="sxs-lookup"><span data-stu-id="3d86b-103">Sorting Objects</span></span>

<span data-ttu-id="3d86b-104">È possibile organizzare i dati visualizzati per semplificarne l'analisi usando il `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d86b-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3d86b-105">`Sort-Object` accetta il nome di una o più proprietà da ordinare e restituisce i dati ordinati in base ai valori di tali proprietà.</span><span class="sxs-lookup"><span data-stu-id="3d86b-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="3d86b-106">Ordinamento di base</span><span class="sxs-lookup"><span data-stu-id="3d86b-106">Basic sorting</span></span>

<span data-ttu-id="3d86b-107">Prendere in considerazione di elencare le sottodirectory e i file nella directory corrente.</span><span class="sxs-lookup"><span data-stu-id="3d86b-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="3d86b-108">Se si vuole ordinare **LastWriteTime** e quindi in base **nome**, possiamo farlo digitando:</span><span class="sxs-lookup"><span data-stu-id="3d86b-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="3d86b-109">È anche possibile ordinare gli oggetti a in ordine inverso, specificando il **Descending** parametro opzionale.</span><span class="sxs-lookup"><span data-stu-id="3d86b-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="3d86b-110">Utilizzo di tabelle hash</span><span class="sxs-lookup"><span data-stu-id="3d86b-110">Using hash tables</span></span>

<span data-ttu-id="3d86b-111">È possibile ordinare diverse proprietà in ordine diverso utilizzando le tabelle hash in una matrice.</span><span class="sxs-lookup"><span data-stu-id="3d86b-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="3d86b-112">Ogni tabella hash Usa un' **espressione** chiave per specificare il nome della proprietà come stringa e un **crescente** oppure **decrescente** chiave per specificare l'ordinamento dal `$true` o `$false`.</span><span class="sxs-lookup"><span data-stu-id="3d86b-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="3d86b-113">Il **espressione** chiave è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="3d86b-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="3d86b-114">Il **crescente** oppure **Descending** chiave è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="3d86b-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="3d86b-115">Nell'esempio seguente consente di ordinare gli oggetti in ordine decrescente **LastWriteTime** ordine e crescente **nome** ordine.</span><span class="sxs-lookup"><span data-stu-id="3d86b-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="3d86b-116">È anche possibile impostare un blocco di script il **espressione** chiave.</span><span class="sxs-lookup"><span data-stu-id="3d86b-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="3d86b-117">Quando si esegue il `Sort-Object` cmdlet, viene eseguito il blocco di script e il risultato viene utilizzato per l'ordinamento.</span><span class="sxs-lookup"><span data-stu-id="3d86b-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="3d86b-118">Nell'esempio seguente Ordina in ordine decrescente per l'intervallo di tempo tra gli oggetti **CreationTime** e **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="3d86b-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="3d86b-119">Suggerimenti</span><span class="sxs-lookup"><span data-stu-id="3d86b-119">Tips</span></span>

<span data-ttu-id="3d86b-120">È possibile omettere il **proprietà** nome del parametro come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="3d86b-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="3d86b-121">Inoltre, è possibile fare riferimento a `Sort-Object` mediante il relativo alias predefinito, `sort`:</span><span class="sxs-lookup"><span data-stu-id="3d86b-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="3d86b-122">Le chiavi di hash per l'ordinamento possono essere abbreviate come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="3d86b-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="3d86b-123">In questo esempio, il **e** è l'acronimo **espressione**, il **1!d** è l'acronimo di **decrescente**e il **un** è l'acronimo **crescente**.</span><span class="sxs-lookup"><span data-stu-id="3d86b-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="3d86b-124">Per migliorare la leggibilità, è possibile inserire le tabelle hash in una variabile separata:</span><span class="sxs-lookup"><span data-stu-id="3d86b-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```