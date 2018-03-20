---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="a29d3-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="a29d3-103">The ISESnippetObject</span></span>
  <span data-ttu-id="a29d3-104">Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="a29d3-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="a29d3-105">I membri della raccolta **$psISE.CurrentPowerShellTab.Snippets** sono tutti esempi di oggetti **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="a29d3-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="a29d3-106">Il modo più semplice per creare un frammento di codice consiste nell'usare il cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="a29d3-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="a29d3-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="a29d3-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="a29d3-108">Autore</span><span class="sxs-lookup"><span data-stu-id="a29d3-108">Author</span></span>
  <span data-ttu-id="a29d3-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a29d3-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="a29d3-110">Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.</span><span class="sxs-lookup"><span data-stu-id="a29d3-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="a29d3-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="a29d3-111">CodeFragment</span></span>
  <span data-ttu-id="a29d3-112">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a29d3-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="a29d3-113">Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.</span><span class="sxs-lookup"><span data-stu-id="a29d3-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="a29d3-114">Collegamento</span><span class="sxs-lookup"><span data-stu-id="a29d3-114">Shortcut</span></span>
  <span data-ttu-id="a29d3-115">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a29d3-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="a29d3-116">Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="a29d3-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="a29d3-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a29d3-117">See Also</span></span>
- [<span data-ttu-id="a29d3-118">Oggetto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="a29d3-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="a29d3-119">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a29d3-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="a29d3-120">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="a29d3-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
