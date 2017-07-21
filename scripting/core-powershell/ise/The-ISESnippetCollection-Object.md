---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="f508d-103">Oggetto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="f508d-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="f508d-104">L'oggetto **ISESnippetCollection** è una raccolta di oggetti **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="f508d-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="f508d-105">La raccolta di file associata a un oggetto **PowerShellTab** è un membro di questa classe.</span><span class="sxs-lookup"><span data-stu-id="f508d-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="f508d-106">Un esempio è la raccolta **$psISE.CurrentPowerShellTab.Files**.</span><span class="sxs-lookup"><span data-stu-id="f508d-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="f508d-107">Metodo</span><span class="sxs-lookup"><span data-stu-id="f508d-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="f508d-108">Load\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="f508d-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="f508d-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f508d-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="f508d-110">Carica un file snippets.ps1xml contenente frammenti di codice definiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="f508d-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="f508d-111">Il modo più semplice per creare frammenti di codice consiste nell'usare il cmdlet New-IseSnippet, che li archivia automaticamente nella cartella del profilo in modo che vengano caricati ogni volta che si avvia Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f508d-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="f508d-112">**FilePathName**: la stringa specifica il percorso e il nome di un file snippets.ps1xml che contiene le definizioni dei frammenti di codice.</span><span class="sxs-lookup"><span data-stu-id="f508d-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="f508d-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f508d-113">See Also</span></span>
- [<span data-ttu-id="f508d-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="f508d-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="f508d-115">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f508d-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="f508d-116">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f508d-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="f508d-117">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="f508d-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
