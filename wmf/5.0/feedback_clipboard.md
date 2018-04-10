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
# <a name="clipboard-cmdlets"></a><span data-ttu-id="d2972-102">Cmdlet Clipboard</span><span class="sxs-lookup"><span data-stu-id="d2972-102">Clipboard cmdlets</span></span>
<span data-ttu-id="d2972-103">**Get-Clipboard** e **Set-Clipboard** rendono più semplice il trasferimento del contenuto in e da una sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d2972-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="d2972-104">Se ad esempio si usa Esplora risorse per copiare tre file negli Appunti (selezionandoli e premendo `ctrl-c` ad esempio), è possibile accedere facilmente al contenuto degli Appunti come elenco di file:</span><span class="sxs-lookup"><span data-stu-id="d2972-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="d2972-105">I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.</span><span class="sxs-lookup"><span data-stu-id="d2972-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>