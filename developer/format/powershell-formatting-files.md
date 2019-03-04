---
title: Windows PowerShell la formattazione di file | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 35efd36fd70c209e3cbeb9eff0ddf978615fffd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854267"
---
# <a name="windows-powershell-formatting-files"></a>File di formattazione di Windows PowerShell

Windows PowerShell fornisce diversi file di formattazione (. format.ps1xml) che si trovano nella directory di installazione (`$pshome`). Ognuno di questi file definisce la visualizzazione predefinita per un set specifico di oggetti .NET. Questi file non devono mai essere modificati. Tuttavia, è possibile utilizzare tali come riferimento per la creazione di propri file di formattazione personalizzati.

Certificate.Format.ps1xml definisce la visualizzazione degli oggetti nell'archivio certificati, ad esempio i certificati x.509 e gli archivi certificati.

Viene definita la visualizzazione di vari oggetti di .NET, ad esempio oggetti CultureInfo, FileVersionInfo ed EventLogEntry DotNetTypes.Format.ps1xml.

FileSystem.Format.ps1xml definiscono la visualizzazione degli oggetti del file system, ad esempio gli oggetti di file e directory.

Help.Format.ps1xml definisce le diverse visualizzazioni utilizzate per la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, ad esempio le visualizzazioni dettagliate, esempio, i parametri e full.
Definisce le diverse viste usate dal [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, ad esempio le visualizzazioni dettagliate, esempio, i parametri e full.

PowerShellCore.Format.ps1xml definisce la visualizzazione degli oggetti generati dal cmdlet di sistema di Windows PowerShell, ad esempio gli oggetti restituiti dai [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) e [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet.
Definisce la visualizzazione degli oggetti generati dal cmdlet di sistema di Windows PowerShell, ad esempio gli oggetti restituiti dai [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) e [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet.

PowerShellTrace.Format.ps1xml definisce la visualizzazione degli oggetti di traccia, ad esempio quelle generate dal [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.
Definisce la visualizzazione degli oggetti di traccia, ad esempio quelle generate dal [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

Registry.Format.ps1xml definisce la visualizzazione degli oggetti del Registro di sistema, ad esempio gli oggetti chiave e voce.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
