---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Miglioramenti della console in WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855506"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="60fcb-103">Miglioramenti della console in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="60fcb-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="60fcb-104">Miglioramenti apportati alla console di PowerShell</span><span class="sxs-lookup"><span data-stu-id="60fcb-104">PowerShell console improvements</span></span>

<span data-ttu-id="60fcb-105">Per migliorare l'uso della console, sono state apportate a powershell.exe in WMF 5.1 le modifiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="60fcb-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="60fcb-106">Supporto per VT100</span><span class="sxs-lookup"><span data-stu-id="60fcb-106">VT100 support</span></span>

<span data-ttu-id="60fcb-107">Windows 10 ha aggiunto il supporto per le [sequenze di escape VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="60fcb-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="60fcb-108">Quando si calcola la larghezza delle tabelle, PowerShell ignorerà determinate sequenze di escape di formattazione VT100.</span><span class="sxs-lookup"><span data-stu-id="60fcb-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="60fcb-109">PowerShell ha inoltre aggiunto una nuova API che può essere usata per la formattazione di codice in modo da determinare se VT100 è supportato.</span><span class="sxs-lookup"><span data-stu-id="60fcb-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="60fcb-110">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="60fcb-110">For example:</span></span>

```powershell
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

<span data-ttu-id="60fcb-111">Ecco un [esempio](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo che può essere usato per evidenziare le corrispondenze di `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="60fcb-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="60fcb-112">Salvare l'esempio in un file denominato `MatchInfo.format.ps1xml` quindi per usarlo, nel profilo o altrove, eseguire `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="60fcb-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="60fcb-113">Si noti che le sequenze di escape VT100 sono supportate solo a partire dall'aggiornamento dell'anniversario di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="60fcb-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="60fcb-114">Non sono supportate nei sistemi precedenti.</span><span class="sxs-lookup"><span data-stu-id="60fcb-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="60fcb-115">Supporto della modalità vi in PSReadline</span><span class="sxs-lookup"><span data-stu-id="60fcb-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="60fcb-116">[PSReadline](https://github.com/PowerShell/PSReadLine) aggiunge il supporto per la modalità vi.</span><span class="sxs-lookup"><span data-stu-id="60fcb-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="60fcb-117">Per usare la modalità vi, eseguire `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="60fcb-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="60fcb-118">Stdin reindirizzato con input interattivo</span><span class="sxs-lookup"><span data-stu-id="60fcb-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="60fcb-119">Nelle versioni precedenti, veniva richiesto l'avvio di PowerShell con `powershell -File -` quando stdin veniva reindirizzato e si volevano immettere i comandi in modo interattivo.</span><span class="sxs-lookup"><span data-stu-id="60fcb-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="60fcb-120">Con WMF 5.1, questa opzione di difficile individuazione non è più necessaria.</span><span class="sxs-lookup"><span data-stu-id="60fcb-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="60fcb-121">È possibile avviare PowerShell senza opzioni.</span><span class="sxs-lookup"><span data-stu-id="60fcb-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="60fcb-122">Si noti che PSReadline non supporta stdin reindirizzato e la funzionalità di modifica della riga di comando integrata con stdin reindirizzato è estremamente limitata, ad esempio non è possibile usare i tasti di direzione.</span><span class="sxs-lookup"><span data-stu-id="60fcb-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="60fcb-123">Questo problema verrà risolto nella versione successiva di PSReadline.</span><span class="sxs-lookup"><span data-stu-id="60fcb-123">A future release of PSReadline should address this issue.</span></span>