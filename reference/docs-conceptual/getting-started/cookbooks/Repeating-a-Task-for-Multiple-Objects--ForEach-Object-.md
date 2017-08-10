---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Ripetizione di un&quot;attività per più oggetti ForEach-Object"
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 33ae2c76a512a651ba1b91d15d876608f0d43ccc
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="64f8e-103">Ripetizione di un'attività per più oggetti (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="64f8e-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>
<span data-ttu-id="64f8e-104">Il cmdlet **ForEach-Object** usa blocchi di script e il descrittore $_ per l'oggetto pipeline corrente per consentire l'esecuzione di un comando in ogni oggetto della pipeline.</span><span class="sxs-lookup"><span data-stu-id="64f8e-104">The **ForEach-Object** cmdlet uses script blocks and the $_ descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="64f8e-105">Può essere usato per eseguire alcune attività complesse.</span><span class="sxs-lookup"><span data-stu-id="64f8e-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="64f8e-106">Un caso in cui può risultare utile è la manipolazione dei dati per renderli più utili.</span><span class="sxs-lookup"><span data-stu-id="64f8e-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="64f8e-107">Ad esempio, la classe Win32_LogicalDisk di WMI può essere usata per restituire informazioni sullo spazio disponibile per ogni disco locale.</span><span class="sxs-lookup"><span data-stu-id="64f8e-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="64f8e-108">Tuttavia, i dati vengono restituiti in termini di byte, cosa che rende difficile la lettura:</span><span class="sxs-lookup"><span data-stu-id="64f8e-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="64f8e-109">È possibile convertire il valore FreeSpace in megabyte dividendo due volte ogni valore per 1024. Dopo la prima divisione, i dati saranno in kilobyte e dopo la seconda divisione saranno in megabyte.</span><span class="sxs-lookup"><span data-stu-id="64f8e-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="64f8e-110">È possibile eseguire questa operazione in un blocco di script ForEach-Object digitando:</span><span class="sxs-lookup"><span data-stu-id="64f8e-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="64f8e-111">Purtroppo, adesso l'output consiste di dati senza etichetta associata.</span><span class="sxs-lookup"><span data-stu-id="64f8e-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="64f8e-112">Poiché le proprietà WMI come questa sono di sola lettura, non è possibile convertire direttamente FreeSpace.</span><span class="sxs-lookup"><span data-stu-id="64f8e-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="64f8e-113">Se si digita:</span><span class="sxs-lookup"><span data-stu-id="64f8e-113">If you type this:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="64f8e-114">Si riceve un messaggio di errore:</span><span class="sxs-lookup"><span data-stu-id="64f8e-114">You get an error message:</span></span>

```
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="64f8e-115">È possibile riorganizzare i dati usando alcune tecniche avanzate, ma un approccio più semplice consiste nel creare un nuovo oggetto, usando **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="64f8e-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>
