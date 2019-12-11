---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEFileCollection
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030526"
---
# <a name="the-isefilecollection-object"></a>Oggetto ISEFileCollection

L'oggetto **ISEFileCollection** è una raccolta di oggetti **ISEFile**. Un esempio è la raccolta $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Metodi

### <a name="add-fullpath-"></a>Add\( \[fullPath\]\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Crea e restituisce un nuovo file senza nome e lo aggiunge alla raccolta. La proprietà **IsUntitled** del file appena creato è **$true**.

**\[fullPath\]** : stringa facoltativa che specifica il percorso completo del file. Viene generata un'eccezione se si includono il parametro **fullPath** e un percorso relativo o se si usa un nome di file anziché il percorso completo.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\]\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Rimuove un file specificato dalla scheda PowerShell corrente.

**File**: stringa che specifica il file ISEFile che si vuole rimuovere dalla raccolta. Se il file non è stato salvato, questo metodo genera un'eccezione. Usare il parametro opzionale **Force** per forzare la rimozione di un file non salvato.

**\[Force\]** : valore booleano facoltativo, che se impostato su **$true**, concede l'autorizzazione necessaria per rimuovere il file anche se non è stato salvato dopo l'ultimo uso. Il valore predefinito è **$false**.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Seleziona il file specificato dal parametro **selectedFile**.

**selectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile specifica il file ISEFile che si vuole selezionare.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISEFile](The-ISEFile-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
