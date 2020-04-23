---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISEFile
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736999"
---
# <a name="the-isefile-object"></a><span data-ttu-id="21f6a-103">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="21f6a-103">The ISEFile Object</span></span>

<span data-ttu-id="21f6a-104">Un oggetto **ISEFile** rappresenta un file in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="21f6a-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="21f6a-105">È un'istanza della classe **Microsoft.PowerShell.Host.ISE.ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="21f6a-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEFile** class.</span></span> <span data-ttu-id="21f6a-106">Questo argomento elenca i relativi metodi membro e le proprietà del membro.</span><span class="sxs-lookup"><span data-stu-id="21f6a-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="21f6a-107">`$psISE.CurrentFile` e i file nella raccolta File in una scheda di PowerShell sono tutte istanze della classe \*\***Microsoft.PowerShell.Host.ISE.ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="21f6a-107">The `$psISE.CurrentFile` and the files in the Files collection in a PowerShell tab are all instances of the \*\*\*\*Microsoft.PowerShell.Host.ISE.ISEFile\*\* class.</span></span>

## <a name="methods"></a><span data-ttu-id="21f6a-108">Metodi</span><span class="sxs-lookup"><span data-stu-id="21f6a-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="21f6a-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="21f6a-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="21f6a-110">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-111">Salva il file su disco.</span><span class="sxs-lookup"><span data-stu-id="21f6a-111">Saves the file to disk.</span></span>

<span data-ttu-id="21f6a-112">**\[saveEncoding\]** - [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) facoltativo: parametro di codifica caratteri facoltativo da usare per il file salvato.</span><span class="sxs-lookup"><span data-stu-id="21f6a-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="21f6a-113">Il valore predefinito è **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="21f6a-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="21f6a-114">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="21f6a-114">Exceptions</span></span>

- <span data-ttu-id="21f6a-115">**System.IO.IOException**: non è stato possibile salvare il file.</span><span class="sxs-lookup"><span data-stu-id="21f6a-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="21f6a-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="21f6a-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="21f6a-117">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-118">Salva il file con il nome file e la codifica specificati.</span><span class="sxs-lookup"><span data-stu-id="21f6a-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="21f6a-119">**filename** - Stringa Nome da usare per salvare il file.</span><span class="sxs-lookup"><span data-stu-id="21f6a-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="21f6a-120">**\[saveEncoding\]** - [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) facoltativo: parametro di codifica caratteri facoltativo da usare per il file salvato.</span><span class="sxs-lookup"><span data-stu-id="21f6a-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="21f6a-121">Il valore predefinito è **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="21f6a-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="21f6a-122">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="21f6a-122">Exceptions</span></span>

- <span data-ttu-id="21f6a-123">**System.ArgumentNullException**: il parametro **filename** è Null.</span><span class="sxs-lookup"><span data-stu-id="21f6a-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="21f6a-124">**System.ArgumentException**: il parametro **filename** è vuoto.</span><span class="sxs-lookup"><span data-stu-id="21f6a-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="21f6a-125">**System.IO.IOException**: non è stato possibile salvare il file.</span><span class="sxs-lookup"><span data-stu-id="21f6a-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="21f6a-126">Proprietà</span><span class="sxs-lookup"><span data-stu-id="21f6a-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="21f6a-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="21f6a-127">DisplayName</span></span>

<span data-ttu-id="21f6a-128">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-129">Proprietà di sola lettura che ottiene la stringa contenente il nome visualizzato di questo file.</span><span class="sxs-lookup"><span data-stu-id="21f6a-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="21f6a-130">Il nome viene visualizzato nella scheda **File** nella parte superiore dell'editor.</span><span class="sxs-lookup"><span data-stu-id="21f6a-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="21f6a-131">La presenza di un asterisco (`(*)`) alla fine del nome indica che il file contiene modifiche che non sono state salvate.</span><span class="sxs-lookup"><span data-stu-id="21f6a-131">The presence of an asterisk `(*)` at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="21f6a-132">Editor</span><span class="sxs-lookup"><span data-stu-id="21f6a-132">Editor</span></span>

<span data-ttu-id="21f6a-133">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-134">Proprietà di sola lettura che ottiene l'[oggetto editor](The-ISEEditor-Object.md) usato per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="21f6a-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="21f6a-135">Codifica</span><span class="sxs-lookup"><span data-stu-id="21f6a-135">Encoding</span></span>

<span data-ttu-id="21f6a-136">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-137">Proprietà di sola lettura che ottiene la codifica del file originale.</span><span class="sxs-lookup"><span data-stu-id="21f6a-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="21f6a-138">Si tratta di un oggetto **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="21f6a-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="21f6a-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="21f6a-139">FullPath</span></span>

<span data-ttu-id="21f6a-140">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-141">Proprietà di sola lettura che ottiene la stringa che specifica il percorso completo del file aperto.</span><span class="sxs-lookup"><span data-stu-id="21f6a-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="21f6a-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="21f6a-142">IsSaved</span></span>

<span data-ttu-id="21f6a-143">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-144">Proprietà booleana di sola lettura che restituisce `$true` se il file è stato salvato dopo l'ultima modifica.</span><span class="sxs-lookup"><span data-stu-id="21f6a-144">The read-only Boolean property that returns `$true` if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="21f6a-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="21f6a-145">IsUntitled</span></span>

<span data-ttu-id="21f6a-146">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="21f6a-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="21f6a-147">Proprietà di sola lettura che restituisce `$true` se al file non è mai stato assegnato un titolo.</span><span class="sxs-lookup"><span data-stu-id="21f6a-147">The read-only property that returns `$true` if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="21f6a-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="21f6a-148">See Also</span></span>

- [<span data-ttu-id="21f6a-149">Oggetto ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="21f6a-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="21f6a-150">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="21f6a-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="21f6a-151">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="21f6a-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
