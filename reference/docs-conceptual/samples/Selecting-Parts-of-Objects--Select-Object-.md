---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Selezione di parti di oggetti Select Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737169"
---
# <a name="selecting-parts-of-objects-select-object"></a>Selezione di parti di oggetti (Select-Object)

Per creare nuovi oggetti personalizzati di PowerShell contenenti le proprietà selezionate dagli oggetti usati per crearli, è possibile usare il cmdlet `Select-Object`. Digitare il comando seguente per creare un nuovo oggetto che includa solo le proprietà **Name** e **FreeSpace** della classe WMI **Win32_LogicalDisk**:

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

Con `Select-Object` è possibile creare proprietà calcolate. È quindi possibile visualizzare **FreeSpace** in gigabyte anziché in byte.

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
