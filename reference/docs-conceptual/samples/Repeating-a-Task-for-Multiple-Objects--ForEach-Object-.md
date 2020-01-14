---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ripetizione di un'attività per più oggetti ForEach-Object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736880"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Ripetizione di un'attività per più oggetti (ForEach-Object)

Il cmdlet `ForEach-Object` usa blocchi di script e il descrittore `$_` per l'oggetto pipeline corrente per consentire l'esecuzione di un comando in ogni oggetto della pipeline. Può essere usato per eseguire alcune attività complesse.

Un caso in cui può risultare utile è la manipolazione dei dati per renderli più utili. Ad esempio, la classe **Win32_LogicalDisk** di WMI può essere usata per restituire informazioni sullo spazio disponibile per ogni disco locale. Tuttavia, i dati vengono restituiti in termini di byte, cosa che rende difficile la lettura:

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

È possibile convertire il valore **FreeSpace** in megabyte dividendo ogni valore per 1 MB. È possibile eseguire questa operazione in un blocco di script `ForEach-Object` digitando:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

Purtroppo, adesso l'output consiste di dati senza etichetta associata. Poiché le proprietà WMI come questa sono di sola lettura, non è possibile convertire direttamente **FreeSpace**. Se si digita:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

Si riceve un messaggio di errore:

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

È possibile riorganizzare i dati usando alcune tecniche avanzate, ma un approccio più semplice consiste nel creare un nuovo oggetto usando `Select-Object`.
