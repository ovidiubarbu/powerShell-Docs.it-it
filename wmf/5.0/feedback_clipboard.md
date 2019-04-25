---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057299"
---
# <a name="clipboard-cmdlets"></a>Cmdlet Clipboard
**Get-Clipboard** e **Set-Clipboard** rendono più semplice il trasferimento del contenuto in e da una sessione di Windows PowerShell. Se ad esempio si usa Esplora risorse per copiare tre file negli Appunti (selezionandoli e premendo `ctrl-c` ad esempio), è possibile accedere facilmente al contenuto degli Appunti come elenco di file:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.
