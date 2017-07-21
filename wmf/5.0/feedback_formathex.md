---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 0749f942d542f0e10292a49a6bb1fe47c7fd53df
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="format-hex"></a><span data-ttu-id="f01cd-102">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="f01cd-102">Format-Hex</span></span>
<span data-ttu-id="f01cd-103">**Format-Hex** consente di visualizzare dati binari o di testo in formato esadecimale. Vedere [Format-Hex](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/format-hex)</span><span class="sxs-lookup"><span data-stu-id="f01cd-103">**Format-Hex** lets you view text or binary data in hexadecimal format; see [Format-Hex](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/format-hex)</span></span>

## <a name="example-1"></a><span data-ttu-id="f01cd-104">Esempio 1</span><span class="sxs-lookup"><span data-stu-id="f01cd-104">Example 1</span></span>
<span data-ttu-id="f01cd-105">Visualizzare il contenuto di una stringa in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="f01cd-105">View the contents of a string in hexadecimal format.</span></span>

```PowerShell
"This is a very long line to force the line folding in Format-Hex cmdlet" | Format-Hex
```

<span data-ttu-id="f01cd-106">Output</span><span class="sxs-lookup"><span data-stu-id="f01cd-106">Outputs</span></span>
```
PS C:\> This is a very long line to force the line folding in Format-Hex cmdlet" | Format-Hex


           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   54 68 69 73 20 69 73 20 61 20 76 65 72 79 20 6C  This is a very l
00000010   6F 6E 67 20 6C 69 6E 65 20 74 6F 20 66 6F 72 63  ong line to forc
00000020   65 20 74 68 65 20 6C 69 6E 65 20 66 6F 6C 64 69  e the line foldi
00000030   6E 67 20 69 6E 20 46 6F 72 6D 61 74 2D 48 65 78  ng in Format-Hex
00000040   20 63 6D 64 6C 65 74                              cmdlet         


PS C:\>
```

