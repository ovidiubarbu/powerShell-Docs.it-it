---
title: File di formattazione di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365010"
---
# <a name="windows-powershell-formatting-files"></a>File di formattazione di Windows PowerShell

Windows PowerShell fornisce diversi file di formattazione (format. ps1xml) che si trovano nella directory di installazione (`$pshome`). Ognuno di questi file definisce la visualizzazione predefinita per un set specifico di oggetti .NET. Questi file non devono mai essere modificati. Tuttavia, è possibile utilizzarli come riferimento per la creazione di file di formattazione personalizzati.

`Certificate.Format.ps1xml` definisce la visualizzazione degli oggetti nell'archivio certificati, ad esempio certificati x. 509 e archivi certificati.

`DotNetTypes.Format.ps1xml` definisce la visualizzazione di oggetti .NET diversi, ad esempio gli oggetti CultureInfo, FileVersionInfo e EventLogEntry.

`FileSystem.Format.ps1xml` definisce la visualizzazione di oggetti file system, ad esempio oggetti file e directory.

`Help.Format.ps1xml` definisce le diverse visualizzazioni utilizzate dal cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) , ad esempio le visualizzazioni dettagliate, complete, dei parametri e di esempio.

`PowerShellCore.Format.ps1xml` definisce la visualizzazione degli oggetti generati dai cmdlet di base di Windows PowerShell, ad esempio gli oggetti restituiti dai cmdlet [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) e [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` definisce la visualizzazione di oggetti Trace, ad esempio quelli generati dal cmdlet [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` definisce la visualizzazione degli oggetti del registro di sistema, ad esempio gli oggetti chiave e voce.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
