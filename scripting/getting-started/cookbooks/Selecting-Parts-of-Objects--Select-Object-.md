---
title: Selezione di parti di oggetti (Select-Object)
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 66f2927652b33371aa11db1662d3e9d28b4f5fbd
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="selecting-parts-of-objects-select-object"></a>Selezione di parti di oggetti (Select-Object)
È possibile usare il cmdlet **Select-Object** per creare nuovi oggetti personalizzati di Windows PowerShell contenenti le proprietà selezionate dagli oggetti usati per crearli. Digitare il comando seguente per creare un nuovo oggetto che includa solo le proprietà Name e FreeSpace della classe Win32_LogicalDisk WMI:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Non è possibile visualizzare il tipo di dati dopo l'emissione del comando, ma se si invia tramite pipe il risultato a Get-Member dopo Select-Object, si avrà un nuovo tipo di oggetto, ovvero PSCustomObject:

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

Select-Object può essere usato in diversi modi. Uno di questi consiste nella replica dei dati che è quindi possibile modificare. Adesso è possibile gestire il problema riscontrato nella sezione precedente. È possibile aggiornare il valore di FreeSpace nei nuovi oggetti creati e l'output includerà l'etichetta descrittiva:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

