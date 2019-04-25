---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086749"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="513a5-103">Oggetto ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="513a5-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="513a5-104">L'oggetto **ISEFileCollection** è una raccolta di oggetti **ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="513a5-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="513a5-105">Un esempio è la raccolta $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="513a5-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="513a5-106">Metodi</span><span class="sxs-lookup"><span data-stu-id="513a5-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="513a5-107">Add\( \[fullPath\]\)</span><span class="sxs-lookup"><span data-stu-id="513a5-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="513a5-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="513a5-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="513a5-109">Crea e restituisce un nuovo file senza nome e lo aggiunge alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="513a5-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="513a5-110">La proprietà **IsUntitled** del file appena creato è **$true**.</span><span class="sxs-lookup"><span data-stu-id="513a5-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="513a5-111">**\[fullPath\]**: stringa facoltativa che specifica il percorso completo del file.</span><span class="sxs-lookup"><span data-stu-id="513a5-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="513a5-112">Viene generata un'eccezione se si includono il parametro **fullPath** e un percorso relativo o se si usa un nome di file anziché il percorso completo.</span><span class="sxs-lookup"><span data-stu-id="513a5-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="513a5-113">Remove\( File, \[Force\]\)</span><span class="sxs-lookup"><span data-stu-id="513a5-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="513a5-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="513a5-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="513a5-115">Rimuove un file specificato dalla scheda PowerShell corrente.</span><span class="sxs-lookup"><span data-stu-id="513a5-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="513a5-116">**File**: stringa che specifica il file ISEFile che si vuole rimuovere dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="513a5-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="513a5-117">Se il file non è stato salvato, questo metodo genera un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="513a5-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="513a5-118">Usare il parametro opzionale **Force** per forzare la rimozione di un file non salvato.</span><span class="sxs-lookup"><span data-stu-id="513a5-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="513a5-119">**\[Force\]**: valore booleano facoltativo, che se impostato su **$true**, concede l'autorizzazione necessaria per rimuovere il file anche se non è stato salvato dopo l'ultimo uso.</span><span class="sxs-lookup"><span data-stu-id="513a5-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="513a5-120">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="513a5-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="513a5-121">SetSelectedFile\( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="513a5-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="513a5-122">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="513a5-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="513a5-123">Seleziona il file specificato dal parametro **selectedFile**.</span><span class="sxs-lookup"><span data-stu-id="513a5-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="513a5-124">**selectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile specifica il file ISEFile che si vuole selezionare.</span><span class="sxs-lookup"><span data-stu-id="513a5-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="513a5-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="513a5-125">See Also</span></span>

- [<span data-ttu-id="513a5-126">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="513a5-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="513a5-127">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="513a5-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="513a5-128">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="513a5-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)