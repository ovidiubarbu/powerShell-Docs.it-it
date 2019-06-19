---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetObject
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028896"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="f8a0c-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="f8a0c-103">The ISESnippetObject</span></span>

<span data-ttu-id="f8a0c-104">Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="f8a0c-105">I membri della raccolta **$psISE.CurrentPowerShellTab.Snippets** sono tutti esempi di oggetti **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="f8a0c-106">Il modo più semplice per creare un frammento di codice consiste nell'usare il cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="f8a0c-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="f8a0c-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="f8a0c-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="f8a0c-108">Autore</span><span class="sxs-lookup"><span data-stu-id="f8a0c-108">Author</span></span>

<span data-ttu-id="f8a0c-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a0c-110">Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="f8a0c-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="f8a0c-111">CodeFragment</span></span>

<span data-ttu-id="f8a0c-112">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a0c-113">Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="f8a0c-114">Collegamento</span><span class="sxs-lookup"><span data-stu-id="f8a0c-114">Shortcut</span></span>

<span data-ttu-id="f8a0c-115">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a0c-116">Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="f8a0c-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="f8a0c-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8a0c-117">See Also</span></span>

- [<span data-ttu-id="f8a0c-118">Oggetto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="f8a0c-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="f8a0c-119">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f8a0c-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="f8a0c-120">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="f8a0c-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
