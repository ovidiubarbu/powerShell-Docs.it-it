---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Selezione di parti di oggetti Select Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737169"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="74204-103">Selezione di parti di oggetti (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="74204-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="74204-104">Per creare nuovi oggetti personalizzati di PowerShell contenenti le proprietà selezionate dagli oggetti usati per crearli, è possibile usare il cmdlet `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="74204-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="74204-105">Digitare il comando seguente per creare un nuovo oggetto che includa solo le proprietà **Name** e **FreeSpace** della classe WMI **Win32_LogicalDisk**:</span><span class="sxs-lookup"><span data-stu-id="74204-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="74204-106">Con `Select-Object` è possibile creare proprietà calcolate.</span><span class="sxs-lookup"><span data-stu-id="74204-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="74204-107">È quindi possibile visualizzare **FreeSpace** in gigabyte anziché in byte.</span><span class="sxs-lookup"><span data-stu-id="74204-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
