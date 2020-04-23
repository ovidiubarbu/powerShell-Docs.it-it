---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ripetizione di un'attività per più oggetti ForEach-Object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736880"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="01c43-103">Ripetizione di un'attività per più oggetti (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="01c43-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="01c43-104">Il cmdlet `ForEach-Object` usa blocchi di script e il descrittore `$_` per l'oggetto pipeline corrente per consentire l'esecuzione di un comando in ogni oggetto della pipeline.</span><span class="sxs-lookup"><span data-stu-id="01c43-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="01c43-105">Può essere usato per eseguire alcune attività complesse.</span><span class="sxs-lookup"><span data-stu-id="01c43-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="01c43-106">Un caso in cui può risultare utile è la manipolazione dei dati per renderli più utili.</span><span class="sxs-lookup"><span data-stu-id="01c43-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="01c43-107">Ad esempio, la classe **Win32_LogicalDisk** di WMI può essere usata per restituire informazioni sullo spazio disponibile per ogni disco locale.</span><span class="sxs-lookup"><span data-stu-id="01c43-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="01c43-108">Tuttavia, i dati vengono restituiti in termini di byte, cosa che rende difficile la lettura:</span><span class="sxs-lookup"><span data-stu-id="01c43-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="01c43-109">È possibile convertire il valore **FreeSpace** in megabyte dividendo ogni valore per 1 MB.</span><span class="sxs-lookup"><span data-stu-id="01c43-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="01c43-110">È possibile eseguire questa operazione in un blocco di script `ForEach-Object` digitando:</span><span class="sxs-lookup"><span data-stu-id="01c43-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="01c43-111">Purtroppo, adesso l'output consiste di dati senza etichetta associata.</span><span class="sxs-lookup"><span data-stu-id="01c43-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="01c43-112">Poiché le proprietà WMI come questa sono di sola lettura, non è possibile convertire direttamente **FreeSpace**.</span><span class="sxs-lookup"><span data-stu-id="01c43-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="01c43-113">Se si digita:</span><span class="sxs-lookup"><span data-stu-id="01c43-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="01c43-114">Si riceve un messaggio di errore:</span><span class="sxs-lookup"><span data-stu-id="01c43-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="01c43-115">È possibile riorganizzare i dati usando alcune tecniche avanzate, ma un approccio più semplice consiste nel creare un nuovo oggetto usando `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="01c43-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
