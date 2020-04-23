---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISEFileCollection
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736216"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="342ea-103">Oggetto ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="342ea-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="342ea-104">L'oggetto **ISEFileCollection** è una raccolta di oggetti **ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="342ea-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="342ea-105">Un esempio è la raccolta `$psISE.CurrentPowerShellTab.Files`.</span><span class="sxs-lookup"><span data-stu-id="342ea-105">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="342ea-106">Metodi</span><span class="sxs-lookup"><span data-stu-id="342ea-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="342ea-107">Add\( \[FullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="342ea-107">Add\( \[FullPath\] \)</span></span>

<span data-ttu-id="342ea-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="342ea-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="342ea-109">Crea e restituisce un nuovo file senza nome e lo aggiunge alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="342ea-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="342ea-110">La proprietà **IsUntitled** del file appena creato è `$true`.</span><span class="sxs-lookup"><span data-stu-id="342ea-110">The **IsUntitled** property of the newly created file is `$true`.</span></span>

<span data-ttu-id="342ea-111">**\[FullPath\]** : stringa facoltativa che specifica il percorso completo del file.</span><span class="sxs-lookup"><span data-stu-id="342ea-111">**\[FullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="342ea-112">Viene generata un'eccezione se si includono il parametro **FullPath** e un percorso relativo o se si usa un nome file anziché il percorso completo.</span><span class="sxs-lookup"><span data-stu-id="342ea-112">An exception is generated if you include the **FullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="342ea-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="342ea-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="342ea-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="342ea-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="342ea-115">Rimuove un file specificato dalla scheda PowerShell corrente.</span><span class="sxs-lookup"><span data-stu-id="342ea-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="342ea-116">**File**: stringa che specifica il file ISEFile che si vuole rimuovere dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="342ea-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="342ea-117">Se il file non è stato salvato, questo metodo genera un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="342ea-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="342ea-118">Usare il parametro opzionale **Force** per forzare la rimozione di un file non salvato.</span><span class="sxs-lookup"><span data-stu-id="342ea-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="342ea-119">**\[Force\]** : valore booleano facoltativo che se impostato su `$true` concede l'autorizzazione necessaria per rimuovere il file anche se non è stato salvato dopo l'ultimo uso.</span><span class="sxs-lookup"><span data-stu-id="342ea-119">**\[Force\]** - optional Boolean If set to `$true`, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="342ea-120">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="342ea-120">The default is `$false`.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="342ea-121">SetSelectedFile\( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="342ea-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="342ea-122">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="342ea-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="342ea-123">Seleziona il file specificato dal parametro **SelectedFile**.</span><span class="sxs-lookup"><span data-stu-id="342ea-123">Selects the file that is specified by the **SelectedFile** parameter.</span></span>

<span data-ttu-id="342ea-124">**SelectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile specifica il file ISEFile che si vuole selezionare.</span><span class="sxs-lookup"><span data-stu-id="342ea-124">**SelectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="342ea-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="342ea-125">See Also</span></span>

- [<span data-ttu-id="342ea-126">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="342ea-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="342ea-127">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="342ea-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="342ea-128">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="342ea-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
