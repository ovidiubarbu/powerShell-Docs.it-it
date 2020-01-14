---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737084"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="0b537-103">Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console</span><span class="sxs-lookup"><span data-stu-id="0b537-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="0b537-104">La funzionalità di completamento tramite tasto TAB offre supporto automatico durante la digitazione nel riquadro di script o nel riquadro dei comandi.</span><span class="sxs-lookup"><span data-stu-id="0b537-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="0b537-105">Per sfruttare i vantaggi di questa funzionalità, procedere come segue:</span><span class="sxs-lookup"><span data-stu-id="0b537-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="0b537-106">Per completare automaticamente una voce di comando</span><span class="sxs-lookup"><span data-stu-id="0b537-106">To automatically complete a command entry</span></span>

<span data-ttu-id="0b537-107">Nel riquadro dei comandi o nel riquadro di script digitare alcuni caratteri di un comando e quindi premere <kbd>TAB</kbd> per selezionare il testo di completamento desiderato.</span><span class="sxs-lookup"><span data-stu-id="0b537-107">In the Command Pane or Script Pane, type a few characters of a command and then press <kbd>TAB</kbd> to select the desired completion text.</span></span> <span data-ttu-id="0b537-108">Se più elementi iniziano con il testo digitato originariamente, continuare a premere <kbd>TAB</kbd> fino a quando non verrà visualizzato l'elemento desiderato.</span><span class="sxs-lookup"><span data-stu-id="0b537-108">If multiple items begin with the text that you initially typed, then continue pressing <kbd>TAB</kbd> until the item you want appears.</span></span> <span data-ttu-id="0b537-109">La funzionalità di completamento tramite tasto TAB consente di digitare il nome di un cmdlet, il nome di un parametro, il nome di una variabile, il nome di una proprietà oggetto o il percorso di un file.</span><span class="sxs-lookup"><span data-stu-id="0b537-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="0b537-110">Premendo <kbd>TAB</kbd> nel riquadro di script verrà automaticamente completato un comando solo durante la modifica dei file con estensione `.ps1`, `.psd1` o `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="0b537-110">In the Script Pane, pressing <kbd>TAB</kbd> will automatically complete a command only when you are editing `.ps1`, `.psd1`, or `.psm1` files.</span></span> <span data-ttu-id="0b537-111">La funzionalità di completamento tramite tasto TAB funziona in qualsiasi momento durante la digitazione nel riquadro dei comandi.</span><span class="sxs-lookup"><span data-stu-id="0b537-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="0b537-112">Per completare automaticamente una voce di parametro cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b537-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="0b537-113">Nel riquadro dei comandi o nel riquadro di script digitare un cmdlet seguito da un trattino e quindi premere <kbd>TAB</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0b537-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press <kbd>TAB</kbd>.</span></span>

<span data-ttu-id="0b537-114">Ad esempio digitare `Get-Process -` e quindi premere più volte <kbd>TAB</kbd> per visualizzare ognuno dei parametri per il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b537-114">For example, type `Get-Process -` and then press <kbd>TAB</kbd> multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b537-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0b537-115">See Also</span></span>

- [<span data-ttu-id="0b537-116">Introduzione a Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0b537-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="0b537-117">Come creare una scheda di PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b537-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
