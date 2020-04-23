---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ordinamento degli oggetti
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030778"
---
# <a name="sorting-objects"></a><span data-ttu-id="63dba-103">Ordinamento degli oggetti</span><span class="sxs-lookup"><span data-stu-id="63dba-103">Sorting Objects</span></span>

<span data-ttu-id="63dba-104">È possibile organizzare i dati visualizzati per semplificarne l'analisi usando il cmdlet `Sort-Object`.</span><span class="sxs-lookup"><span data-stu-id="63dba-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="63dba-105">`Sort-Object` acquisisce il nome di una o più proprietà in base a cui ordinare i dati e li restituisce ordinati in base ai valori di tali proprietà.</span><span class="sxs-lookup"><span data-stu-id="63dba-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="63dba-106">Ordinamento di base</span><span class="sxs-lookup"><span data-stu-id="63dba-106">Basic sorting</span></span>

<span data-ttu-id="63dba-107">Si consideri l'esigenza di elencare le sottodirectory e i file nella directory corrente.</span><span class="sxs-lookup"><span data-stu-id="63dba-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="63dba-108">Se si vuole ordinare in base a **LastWriteTime** e poi in base a **Name**, è possibile digitare:</span><span class="sxs-lookup"><span data-stu-id="63dba-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="63dba-109">È anche possibile ordinare gli oggetti in ordine inverso, specificando il parametro **Descending**.</span><span class="sxs-lookup"><span data-stu-id="63dba-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="63dba-110">Uso di tabelle hash</span><span class="sxs-lookup"><span data-stu-id="63dba-110">Using hash tables</span></span>

<span data-ttu-id="63dba-111">È possibile ordinare diversamente proprietà diverse usando le tabelle hash in una matrice.</span><span class="sxs-lookup"><span data-stu-id="63dba-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="63dba-112">Ogni tabella hash usa una chiave **Expression** per specificare il nome della proprietà e una chiave **Ascending** o **Descending** per specificare l'ordinamento `$true` o `$false`.</span><span class="sxs-lookup"><span data-stu-id="63dba-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="63dba-113">La chiave **Expression** è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="63dba-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="63dba-114">La chiave **Ascending** o **Descending** è facoltativa.</span><span class="sxs-lookup"><span data-stu-id="63dba-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="63dba-115">Nell'esempio seguente gli oggetti vengono ordinati in base a **LastWriteTime** (in ordine decrescente) e in base a **Name** (in ordine crescente).</span><span class="sxs-lookup"><span data-stu-id="63dba-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="63dba-116">È anche possibile impostare un blocco di script sulla chiave **Expression**.</span><span class="sxs-lookup"><span data-stu-id="63dba-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="63dba-117">Quando si esegue il cmdlet `Sort-Object` viene eseguito il blocco di script e il risultato viene usato per l'ordinamento.</span><span class="sxs-lookup"><span data-stu-id="63dba-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="63dba-118">L'esempio seguente dispone gli oggetti in ordine decrescente in base all'intervallo di tempo intercorso tra **CreationTime** e **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="63dba-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="63dba-119">Suggerimenti</span><span class="sxs-lookup"><span data-stu-id="63dba-119">Tips</span></span>

<span data-ttu-id="63dba-120">È possibile omettere il nome del parametro **Property** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="63dba-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="63dba-121">È anche possibile fare riferimento a `Sort-Object` tramite il relativo alias predefinito, `sort`:</span><span class="sxs-lookup"><span data-stu-id="63dba-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="63dba-122">Le chiavi nelle tabelle hash per l'ordinamento possono essere abbreviate come segue:</span><span class="sxs-lookup"><span data-stu-id="63dba-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="63dba-123">In questo esempio **e** rappresenta **Expression**, **d** indica **Descending** e **a** **Ascending**.</span><span class="sxs-lookup"><span data-stu-id="63dba-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="63dba-124">Per migliorare la leggibilità, è possibile inserire le tabelle hash in una variabile separata:</span><span class="sxs-lookup"><span data-stu-id="63dba-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
