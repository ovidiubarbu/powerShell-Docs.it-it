---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Selezione di parti di oggetti Select Object
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="c6145-103">Selezione di parti di oggetti (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="c6145-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="c6145-104">È possibile usare il cmdlet **Select-Object** per creare nuovi oggetti personalizzati di Windows PowerShell contenenti le proprietà selezionate dagli oggetti usati per crearli.</span><span class="sxs-lookup"><span data-stu-id="c6145-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="c6145-105">Digitare il comando seguente per creare un nuovo oggetto che includa solo le proprietà Name e FreeSpace della classe Win32_LogicalDisk WMI:</span><span class="sxs-lookup"><span data-stu-id="c6145-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="c6145-106">Non è possibile visualizzare il tipo di dati dopo l'emissione del comando, ma se si invia tramite pipe il risultato a Get-Member dopo Select-Object, si avrà un nuovo tipo di oggetto, ovvero PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="c6145-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="c6145-107">Select-Object può essere usato in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="c6145-107">Select-Object has many uses.</span></span> <span data-ttu-id="c6145-108">Uno di questi consiste nella replica dei dati che è quindi possibile modificare.</span><span class="sxs-lookup"><span data-stu-id="c6145-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="c6145-109">Adesso è possibile gestire il problema riscontrato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="c6145-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="c6145-110">È possibile aggiornare il valore di FreeSpace nei nuovi oggetti creati e l'output includerà l'etichetta descrittiva:</span><span class="sxs-lookup"><span data-stu-id="c6145-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
