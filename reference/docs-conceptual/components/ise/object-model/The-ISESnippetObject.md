---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetObject
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500931"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="bdbb9-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="bdbb9-103">The ISESnippetObject</span></span>

<span data-ttu-id="bdbb9-104">Un oggetto **ISESnippet** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="bdbb9-105">I membri della raccolta `$psISE.CurrentPowerShellTab.Snippets` sono tutti esempi di oggetti **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="bdbb9-106">Il modo più semplice per creare un frammento di codice è l'uso del cmdlet [New-IseSnippet](/powershell/module/ISE/New-IseSnippet).</span><span class="sxs-lookup"><span data-stu-id="bdbb9-106">The easiest way to create a snippet is to use the [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="bdbb9-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="bdbb9-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="bdbb9-108">Autore</span><span class="sxs-lookup"><span data-stu-id="bdbb9-108">Author</span></span>

<span data-ttu-id="bdbb9-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bdbb9-110">Proprietà di sola lettura che ottiene il nome dell'autore del frammento di codice.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="bdbb9-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="bdbb9-111">CodeFragment</span></span>

<span data-ttu-id="bdbb9-112">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bdbb9-113">Proprietà di sola lettura che ottiene il frammento di codice da inserire nell'editor.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="bdbb9-114">Tasto di scelta rapida</span><span class="sxs-lookup"><span data-stu-id="bdbb9-114">Shortcut</span></span>

<span data-ttu-id="bdbb9-115">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bdbb9-116">Proprietà di sola lettura che ottiene il tasto di scelta rapida Windows per la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="bdbb9-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="bdbb9-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bdbb9-117">See Also</span></span>

- [<span data-ttu-id="bdbb9-118">Oggetto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="bdbb9-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="bdbb9-119">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bdbb9-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="bdbb9-120">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="bdbb9-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
