---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951393"
---
# <a name="the-isefile-object"></a>Oggetto ISEFile

Un oggetto **ISEFile** rappresenta un file in Windows PowerShell® Integrated Scripting Environment (ISE). È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEFile. Questo argomento elenca i relativi metodi membro e le proprietà del membro. L'oggetto **$psISE.CurrentFile** e i file nella raccolta File in una scheda di PowerShell sono tutte istanze della classe Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Metodi

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Salva il file su disco.

**\[saveEncoding\]** - [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) facoltativo: parametro di codifica caratteri facoltativo da usare per il file salvato. Il valore predefinito è **UTF8**.

### <a name="exceptions"></a>Eccezioni

- **System.IO.IOException**: non è stato possibile salvare il file.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Salva il file con il nome file e la codifica specificati.

**filename** - Stringa Nome da usare per salvare il file.

**\[saveEncoding\]** - [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) facoltativo: parametro di codifica caratteri facoltativo da usare per il file salvato. Il valore predefinito è **UTF8**.

### <a name="exceptions"></a>Eccezioni

- **System.ArgumentNullException**: il parametro **filename** è Null.
- **System.ArgumentException**: il parametro **filename** è vuoto.
- **System.IO.IOException**: non è stato possibile salvare il file.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Proprietà

### <a name="displayname"></a>DisplayName

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene la stringa contenente il nome visualizzato di questo file. Il nome viene visualizzato nella scheda **File** nella parte superiore dell'editor. La presenza di un asterisco \(\*\) alla fine del nome indica che il file contiene modifiche che non sono state salvate.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene l'[oggetto editor](The-ISEEditor-Object.md) usato per il file specificato.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encoding

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene la codifica del file originale. Si tratta di un oggetto **System.Text.Encoding**.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene la stringa che specifica il percorso completo del file aperto.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà booleana di sola lettura che restituisce **$true** se il file è stato salvato dopo l'ultima modifica.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che restituisce **$true** se al file non è mai stato assegnato un titolo.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)