---
title: Selezione di parti di oggetti Select-Object
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: c5ec8b902096f85e4d5f5575587434f2adf7c6a1

---

# Selezione di parti di oggetti (Select-Object)
È possibile usare il cmdlet **Select\-Object** per creare nuovi oggetti personalizzati di Windows PowerShell contenenti le proprietà selezionate dagli oggetti usati per crearli. Digitare il comando seguente per creare un nuovo oggetto che includa solo le proprietà Name e FreeSpace della classe WMI Win32\_LogicalDisk:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Non è possibile visualizzare il tipo di dati dopo l'emissione del comando, ma se si invia tramite pipe il risultato a Get\-Member dopo Select\-Object, si avrà un nuovo tipo di oggetto, ovvero PSCustomObject:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Select\-Object può essere usato in diversi modi. Uno di questi consiste nella replica dei dati che è quindi possibile modificare. Adesso è possibile gestire il problema riscontrato nella sezione precedente. È possibile aggiornare il valore di FreeSpace nei nuovi oggetti creati e l'output includerà l'etichetta descrittiva:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```




<!--HONumber=Jun16_HO4-->


