---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Miglioramenti della console in WMF 5.1
ms.openlocfilehash: 2abc02010c6c1d9f7fc617e9831b2d1243e0a3ee
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="1e70c-103">Miglioramenti della console in WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="1e70c-103">Console Improvements in WMF 5.1#</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="1e70c-104">Miglioramenti apportati alla console di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e70c-104">PowerShell console improvements</span></span>

<span data-ttu-id="1e70c-105">Per migliorare l'uso della console, sono state apportate a powershell.exe in WMF 5.1 le modifiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="1e70c-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="1e70c-106">Supporto per VT100</span><span class="sxs-lookup"><span data-stu-id="1e70c-106">VT100 support</span></span>

<span data-ttu-id="1e70c-107">Windows 10 ha aggiunto il supporto per le [sequenze di escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1e70c-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="1e70c-108">Quando si calcola la larghezza delle tabelle, PowerShell ignorerà determinate sequenze di escape di formattazione VT100.</span><span class="sxs-lookup"><span data-stu-id="1e70c-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="1e70c-109">PowerShell ha inoltre aggiunto una nuova API che può essere usata per la formattazione di codice in modo da determinare se VT100 è supportato.</span><span class="sxs-lookup"><span data-stu-id="1e70c-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="1e70c-110">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="1e70c-110">For example:</span></span>

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
<span data-ttu-id="1e70c-111">Ecco un [esempio](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo che può essere usato per evidenziare le corrispondenze di Select-String.</span><span class="sxs-lookup"><span data-stu-id="1e70c-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="1e70c-112">Salvare l'esempio in un file denominato `MatchInfo.format.ps1xml` quindi per usarlo, nel profilo o altrove, eseguire `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="1e70c-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="1e70c-113">Si noti che le sequenze di escape VT100 sono supportate solo a partire dall'aggiornamento Aniversary di Windows 10. Non sono supportate nei sistemi precedenti.</span><span class="sxs-lookup"><span data-stu-id="1e70c-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="1e70c-114">Supporto della modalità vi in PSReadline</span><span class="sxs-lookup"><span data-stu-id="1e70c-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="1e70c-115">[PSReadline](https://github.com/lzybkr/PSReadLine) aggiunge il supporto per la modalità vi.</span><span class="sxs-lookup"><span data-stu-id="1e70c-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="1e70c-116">Per usare la modalità vi, eseguire `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="1e70c-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="1e70c-117">Stdin reindirizzato con input interattivo</span><span class="sxs-lookup"><span data-stu-id="1e70c-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="1e70c-118">Nelle versioni precedenti, veniva richiesto l'avvio di PowerShell con `powershell -File -` quando stdin veniva reindirizzato e si volevano immettere i comandi in modo interattivo.</span><span class="sxs-lookup"><span data-stu-id="1e70c-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="1e70c-119">Con WMF 5.1, questa opzione di difficile individuazione non è più necessaria.</span><span class="sxs-lookup"><span data-stu-id="1e70c-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="1e70c-120">È possibile avviare PowerShell senza opzioni, ad esempio `powershell`.</span><span class="sxs-lookup"><span data-stu-id="1e70c-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="1e70c-121">Si noti che PSReadline al momento non supporta stdin reindirizzato e la funzionalità di modifica della riga di comando integrata con stdin reindirizzato è estremamente limitata, ad esempio non è possibile usare i tasti di direzione.</span><span class="sxs-lookup"><span data-stu-id="1e70c-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="1e70c-122">Questo problema verrà risolto nella versione successiva di PSReadline.</span><span class="sxs-lookup"><span data-stu-id="1e70c-122">A future release of PSReadline should address this issue.</span></span>