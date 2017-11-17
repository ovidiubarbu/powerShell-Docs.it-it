---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="e1f08-103">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="e1f08-103">The ISEFile Object</span></span>
  <span data-ttu-id="e1f08-104">Un oggetto **ISEFile** rappresenta un file in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="e1f08-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="e1f08-105">È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="e1f08-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="e1f08-106">Questo argomento elenca i relativi metodi membro e le proprietà del membro.</span><span class="sxs-lookup"><span data-stu-id="e1f08-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="e1f08-107">L'oggetto **$psISE.CurrentFile** e i file nella raccolta File in una scheda di PowerShell sono tutte istanze della classe Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="e1f08-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="e1f08-108">Metodo</span><span class="sxs-lookup"><span data-stu-id="e1f08-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="e1f08-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="e1f08-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="e1f08-110">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-111">Salva il file su disco.</span><span class="sxs-lookup"><span data-stu-id="e1f08-111">Saves the file to disk.</span></span>

 <span data-ttu-id="e1f08-112">**\[saveEncoding\]** - [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) facoltativo: parametro di codifica caratteri facoltativo da usare per il file salvato.</span><span class="sxs-lookup"><span data-stu-id="e1f08-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="e1f08-113">Il valore predefinito è **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="e1f08-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="e1f08-114">**Eccezioni**</span><span class="sxs-lookup"><span data-stu-id="e1f08-114">**Exceptions**</span></span>
 -   <span data-ttu-id="e1f08-115">**System.IO.IOException**: non è stato possibile salvare il file.</span><span class="sxs-lookup"><span data-stu-id="e1f08-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="e1f08-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="e1f08-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="e1f08-117">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-118">Salva il file con il nome file e la codifica specificati.</span><span class="sxs-lookup"><span data-stu-id="e1f08-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="e1f08-119">**filename** - Stringa Nome da usare per salvare il file.</span><span class="sxs-lookup"><span data-stu-id="e1f08-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="e1f08-120">**\[saveEncoding\]** - [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) facoltativo: parametro di codifica caratteri facoltativo da usare per il file salvato.</span><span class="sxs-lookup"><span data-stu-id="e1f08-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="e1f08-121">Il valore predefinito è **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="e1f08-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="e1f08-122">**Eccezioni**</span><span class="sxs-lookup"><span data-stu-id="e1f08-122">**Exceptions**</span></span>
 -   <span data-ttu-id="e1f08-123">**System.ArgumentNullException**: il parametro **filename** è Null.</span><span class="sxs-lookup"><span data-stu-id="e1f08-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="e1f08-124">**System.ArgumentException**: il parametro **filename** è vuoto.</span><span class="sxs-lookup"><span data-stu-id="e1f08-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="e1f08-125">**System.IO.IOException**: non è stato possibile salvare il file.</span><span class="sxs-lookup"><span data-stu-id="e1f08-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="e1f08-126">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e1f08-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="e1f08-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e1f08-127">DisplayName</span></span>
  <span data-ttu-id="e1f08-128">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="e1f08-129">Proprietà di sola lettura che ottiene la stringa contenente il nome visualizzato di questo file.</span><span class="sxs-lookup"><span data-stu-id="e1f08-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="e1f08-130">Il nome viene visualizzato nella scheda **File** nella parte superiore dell'editor.</span><span class="sxs-lookup"><span data-stu-id="e1f08-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="e1f08-131">La presenza di un asterisco \(\*\) alla fine del nome indica che il file contiene modifiche che non sono state salvate.</span><span class="sxs-lookup"><span data-stu-id="e1f08-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="e1f08-132">Editor</span><span class="sxs-lookup"><span data-stu-id="e1f08-132">Editor</span></span>
  <span data-ttu-id="e1f08-133">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-134">Proprietà di sola lettura che ottiene l'[oggetto editor](The-ISEEditor-Object.md) usato per il file specificato.</span><span class="sxs-lookup"><span data-stu-id="e1f08-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="e1f08-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="e1f08-135">Encoding</span></span>
  <span data-ttu-id="e1f08-136">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-137">Proprietà di sola lettura che ottiene la codifica del file originale.</span><span class="sxs-lookup"><span data-stu-id="e1f08-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="e1f08-138">Si tratta di un oggetto **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="e1f08-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="e1f08-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="e1f08-139">FullPath</span></span>
  <span data-ttu-id="e1f08-140">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-141">Proprietà di sola lettura che ottiene la stringa che specifica il percorso completo del file aperto.</span><span class="sxs-lookup"><span data-stu-id="e1f08-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="e1f08-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="e1f08-142">IsSaved</span></span>
  <span data-ttu-id="e1f08-143">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-144">Proprietà booleana di sola lettura che restituisce **$true** se il file è stato salvato dopo l'ultima modifica.</span><span class="sxs-lookup"><span data-stu-id="e1f08-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="e1f08-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="e1f08-145">IsUntitled</span></span>
  <span data-ttu-id="e1f08-146">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e1f08-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e1f08-147">Proprietà di sola lettura che restituisce **$true** se al file non è mai stato assegnato un titolo.</span><span class="sxs-lookup"><span data-stu-id="e1f08-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="e1f08-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e1f08-148">See Also</span></span>
- [<span data-ttu-id="e1f08-149">Oggetto ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="e1f08-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="e1f08-150">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e1f08-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="e1f08-151">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e1f08-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="e1f08-152">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="e1f08-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
