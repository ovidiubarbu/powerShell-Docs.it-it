---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Ordinamento degli oggetti
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="sorting-objects"></a><span data-ttu-id="09bdf-103">Ordinamento degli oggetti</span><span class="sxs-lookup"><span data-stu-id="09bdf-103">Sorting Objects</span></span>
<span data-ttu-id="09bdf-104">È possibile organizzare i dati visualizzati per semplificarne l'analisi usando il cmdlet **Sort-Object**.</span><span class="sxs-lookup"><span data-stu-id="09bdf-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="09bdf-105">**Sort-Object** acquisisce il nome di una o più proprietà in base a cui ordinare e restituisce i dati ordinati in base ai valori di tali proprietà.</span><span class="sxs-lookup"><span data-stu-id="09bdf-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="09bdf-106">Un esempio può essere costituito dall'esigenza di elencare le istanze Win32_SystemDriver.</span><span class="sxs-lookup"><span data-stu-id="09bdf-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="09bdf-107">Se si vuole ordinare in base a **State** e quindi in base a **Name**, è possibile digitare:</span><span class="sxs-lookup"><span data-stu-id="09bdf-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="09bdf-108">Nonostante si tratti di una visualizzazione estesa, gli elementi con lo stesso stato vengono raggruppati:</span><span class="sxs-lookup"><span data-stu-id="09bdf-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

<span data-ttu-id="09bdf-109">È possibile ordinare gli oggetti anche in ordine inverso, specificando il parametro **Descending**.</span><span class="sxs-lookup"><span data-stu-id="09bdf-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="09bdf-110">L'ordine viene invertito in modo che i nomi vengano ordinati in ordine alfabetico inverso e i numeri vengano ordinati per dimensioni decrescenti.</span><span class="sxs-lookup"><span data-stu-id="09bdf-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

