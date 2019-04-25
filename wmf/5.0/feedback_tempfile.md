---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057852"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
A volte, negli script è necessario creare un file temporaneo. È possibile farlo facilmente con il cmdlet **New-TemporaryFile**:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp
