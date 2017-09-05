---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="925fb-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="925fb-103">The ISESnippetObject</span></span>
  <span data-ttu-id="925fb-104">Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="925fb-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="925fb-105">I membri della raccolta **$psISE.CurrentPowerShellTab.Snippets** sono tutti esempi di oggetti **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="925fb-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="925fb-106">Il modo più semplice per creare un frammento di codice consiste nell'usare il cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="925fb-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="925fb-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="925fb-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="925fb-108">Autore</span><span class="sxs-lookup"><span data-stu-id="925fb-108">Author</span></span>
  <span data-ttu-id="925fb-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="925fb-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="925fb-110">Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.</span><span class="sxs-lookup"><span data-stu-id="925fb-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="925fb-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="925fb-111">CodeFragment</span></span>
  <span data-ttu-id="925fb-112">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="925fb-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="925fb-113">Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.</span><span class="sxs-lookup"><span data-stu-id="925fb-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="925fb-114">Collegamento</span><span class="sxs-lookup"><span data-stu-id="925fb-114">Shortcut</span></span>
  <span data-ttu-id="925fb-115">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="925fb-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="925fb-116">Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="925fb-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="925fb-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="925fb-117">See Also</span></span>
- [<span data-ttu-id="925fb-118">Oggetto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="925fb-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="925fb-119">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="925fb-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="925fb-120">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="925fb-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="925fb-121">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="925fb-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
