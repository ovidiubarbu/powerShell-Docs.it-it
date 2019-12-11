---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISESnippetCollection
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030507"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="88fc6-103">Oggetto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="88fc6-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="88fc6-104">L'oggetto **ISESnippetCollection** è una raccolta di oggetti **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="88fc6-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="88fc6-105">La raccolta di file associata a un oggetto **PowerShellTab** è un membro di questa classe.</span><span class="sxs-lookup"><span data-stu-id="88fc6-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="88fc6-106">Un esempio è la raccolta **$psISE.CurrentPowerShellTab.Files**.</span><span class="sxs-lookup"><span data-stu-id="88fc6-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="88fc6-107">Metodi</span><span class="sxs-lookup"><span data-stu-id="88fc6-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="88fc6-108">Load\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="88fc6-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="88fc6-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="88fc6-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="88fc6-110">Carica un file snippets.ps1xml contenente frammenti di codice definiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="88fc6-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="88fc6-111">Il modo più semplice per creare frammenti di codice consiste nell'usare il cmdlet New-IseSnippet, che li archivia automaticamente nella cartella del profilo in modo che vengano caricati ogni volta che si avvia Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="88fc6-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="88fc6-112">**FilePathName**: la stringa specifica il percorso e il nome di un file snippets.ps1xml che contiene le definizioni dei frammenti di codice.</span><span class="sxs-lookup"><span data-stu-id="88fc6-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="88fc6-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88fc6-113">See Also</span></span>

- [<span data-ttu-id="88fc6-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="88fc6-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="88fc6-115">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="88fc6-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="88fc6-116">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="88fc6-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
