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
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Ripetizione di un'attività per più oggetti (ForEach-Object)
Il cmdlet **ForEach-Object** usa blocchi di script e il descrittore $_ per l'oggetto pipeline corrente per consentire l'esecuzione di un comando in ogni oggetto della pipeline. Può essere usato per eseguire alcune attività complesse.

Un caso in cui può risultare utile è la manipolazione dei dati per renderli più utili. Ad esempio, la classe Win32_LogicalDisk di WMI può essere usata per restituire informazioni sullo spazio disponibile per ogni disco locale. Tuttavia, i dati vengono restituiti in termini di byte, cosa che rende difficile la lettura:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

È possibile convertire il valore FreeSpace in megabyte dividendo due volte ogni valore per 1024. Dopo la prima divisione, i dati saranno in kilobyte e dopo la seconda divisione saranno in megabyte. È possibile eseguire questa operazione in un blocco di script ForEach-Object digitando:

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Purtroppo, adesso l'output consiste di dati senza etichetta associata. Poiché le proprietà WMI come questa sono di sola lettura, non è possibile convertire direttamente FreeSpace. Se si digita:

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Si riceve un messaggio di errore:

```
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

È possibile riorganizzare i dati usando alcune tecniche avanzate, ma un approccio più semplice consiste nel creare un nuovo oggetto, usando **Select-Object**.

