---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEEditor
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952614"
---
# <a name="the-iseeditor-object"></a>Oggetto ISEEditor

Un oggetto **ISEEditor** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEEditor. Il riquadro della console è un oggetto **ISEEditor**. Ogni oggetto [ISEFile](The-ISEFile-Object.md) ha un oggetto **ISEEditor** associato. Le sezioni seguenti elencano i metodi e proprietà di un oggetto **ISEEditor**.

## <a name="methods"></a>Metodi

### <a name="clear"></a>Clear\(\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Cancella il testo nell'editor.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Scorre l'editor in modo che la riga che corrisponde al valore del parametro **lineNumber** specificato sia visibile. Genera un'eccezione se il numero di riga specificato non è compreso nell'intervallo tra 1 e l'ultimo numero di riga, che definisce i numeri di riga validi.

**lineNumber** Numero della riga che deve essere resa visibile.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Imposta lo stato attivo nell'editor.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Ottiene la lunghezza della riga specificata dal numero di riga come valore intero.

**lineNumber** Numero della riga di cui ottenere la lunghezza.

**Returns** Lunghezza della riga in corrispondenza del numero di riga specificato.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Sposta il cursore sul carattere corrispondente se la proprietà **CanGoToMatch** dell'oggetto editor è **$true**, il che si verifica quando il cursore si trova immediatamente prima di una parentesi, di una parentesi quadra o di una parentesi graffa di apertura, \(, \[, { o immediatamente dopo una parentesi, una parentesi quadra o una parentesi graffa di chiusura, \), \], }.  Il cursore viene posizionato prima di un carattere di apertura o dopo un carattere di chiusura. Se la proprietà **CanGoToMatch** è **$false**, questo metodo non esegue alcuna operazione.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( text \)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Sostituisce la selezione con un testo o inserisce il testo nella posizione corrente del cursore.

**text** - Stringa Il testo da inserire.

Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Seleziona il testo dai parametri **startLine**, **startColumn**, **endLine** ed **endColumn**.

**startLine** - Intero La riga in cui inizia la selezione.

**startColumn** - Intero La colonna all'interno della riga di inizio in cui inizia la selezione.

**endLine** - Intero La riga in cui termina la selezione.

**endColumn** - Intero La colonna all'interno della riga di fine in cui termina la selezione.

Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Seleziona l'intera riga di testo che contiene attualmente il cursore.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Imposta la posizione del cursore sul numero di riga e sul numero di colonna. Genera un'eccezione se il numero di riga del cursore o il numero di colonna del cursore non è compreso nei relativi intervalli validi.

**lineNumber** - Intero Il numero di riga del cursore.

**columnNumber** - Intero Il numero di colonna del cursore.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Espande o comprime tutte le sezioni della struttura.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Proprietà

### <a name="cangotomatch"></a>CanGoToMatch

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Proprietà di sola lettura booleana che indica se il cursore si trova accanto a una parentesi, a una parentesi quadra o a una parentesi graffa - \(\), \[\], {}. Se il cursore si trova immediatamente prima del carattere di apertura o immediatamente dopo il carattere di chiusura di una coppia, il valore di questa proprietà è **$true**. In caso contrario, è **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il numero di colonna che corrisponde alla posizione del cursore.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il numero di riga che contiene il cursore.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene la riga completa che contiene il cursore.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il conteggio delle righe dall'editor.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il testo selezionato dall'editor.

Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.

### <a name="text"></a>Testo

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di lettura/scrittura che ottiene o imposta il testo nell'editor.

Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.

## <a name="scripting-example"></a>Esempio di script

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISEFile](The-ISEFile-Object.md)
- [Oggetto PowerShellTab](The-PowerShellTab-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)