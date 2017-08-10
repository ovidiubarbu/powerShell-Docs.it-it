---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 284891c9812a22bb1759678074dc7f967f324c0b
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="0f96e-103">Oggetto ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="0f96e-103">The ISEFileCollection Object</span></span>
  <span data-ttu-id="0f96e-104">L'oggetto **ISEFileCollection** è una raccolta di oggetti **ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="0f96e-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="0f96e-105">Un esempio è la raccolta $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="0f96e-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="0f96e-106">Metodo</span><span class="sxs-lookup"><span data-stu-id="0f96e-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="0f96e-107">Add\( \[fullPath\]\)</span><span class="sxs-lookup"><span data-stu-id="0f96e-107">Add\( \[fullPath\] \)</span></span>
  <span data-ttu-id="0f96e-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="0f96e-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0f96e-109">Crea e restituisce un nuovo file senza nome e lo aggiunge alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="0f96e-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="0f96e-110">La proprietà **IsUntitled** del file appena creato è **$true**.</span><span class="sxs-lookup"><span data-stu-id="0f96e-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

 <span data-ttu-id="0f96e-111">**\[fullPath\]**: stringa facoltativa che specifica il percorso completo del file.</span><span class="sxs-lookup"><span data-stu-id="0f96e-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="0f96e-112">Viene generata un'eccezione se si includono il parametro **fullPath** e un percorso relativo o se si usa un nome di file anziché il percorso completo.</span><span class="sxs-lookup"><span data-stu-id="0f96e-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a><span data-ttu-id="0f96e-113">Remove\( File, \[Force\]\)</span><span class="sxs-lookup"><span data-stu-id="0f96e-113">Remove\( File, \[Force\] \)</span></span>
  <span data-ttu-id="0f96e-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="0f96e-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0f96e-115">Rimuove un file specificato dalla scheda PowerShell corrente.</span><span class="sxs-lookup"><span data-stu-id="0f96e-115">Removes a specified file from the current PowerShell tab.</span></span>

 <span data-ttu-id="0f96e-116">**File**: stringa che specifica il file ISEFile che si vuole rimuovere dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="0f96e-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="0f96e-117">Se il file non è stato salvato, questo metodo genera un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="0f96e-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="0f96e-118">Usare il parametro opzionale **Force** per forzare la rimozione di un file non salvato.</span><span class="sxs-lookup"><span data-stu-id="0f96e-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

 <span data-ttu-id="0f96e-119">**\[Force\]**: valore booleano facoltativo, che se impostato su **$true**, concede l'autorizzazione necessaria per rimuovere il file anche se non è stato salvato dopo l'ultimo uso.</span><span class="sxs-lookup"><span data-stu-id="0f96e-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="0f96e-120">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="0f96e-120">The default is **$false**.</span></span>

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="0f96e-121">SetSelectedFile\( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="0f96e-121">SetSelectedFile\( selectedFile \)</span></span>
  <span data-ttu-id="0f96e-122">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="0f96e-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0f96e-123">Seleziona il file specificato dal parametro **selectedFile**.</span><span class="sxs-lookup"><span data-stu-id="0f96e-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

 <span data-ttu-id="0f96e-124">**selectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile specifica il file ISEFile che si vuole selezionare.</span><span class="sxs-lookup"><span data-stu-id="0f96e-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a><span data-ttu-id="0f96e-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f96e-125">See Also</span></span>
- [<span data-ttu-id="0f96e-126">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="0f96e-126">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="0f96e-127">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0f96e-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="0f96e-128">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0f96e-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="0f96e-129">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="0f96e-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  