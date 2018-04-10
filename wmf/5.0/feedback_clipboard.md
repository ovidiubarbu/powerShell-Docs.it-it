---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: d34a267bae7e48afe4442256d7f112da3a97eb7d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
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