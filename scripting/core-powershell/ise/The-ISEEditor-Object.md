---
title: Oggetto ISEEditor
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
---
# Oggetto ISEEditor
  Un oggetto **ISEEditor** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEEditor. Il riquadro della console è un oggetto **ISEEditor**. Ogni oggetto [ISEFile](The-ISEFile-Object.md) ha un oggetto **ISEEditor** associato. Le sezioni seguenti elencano i metodi e proprietà di un oggetto **ISEEditor**.

## Metodo

### Clear()
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Cancella il testo nell'editor.

```
# Clears the text in the Console pane.
$psIse.CurrentPowerShellTab.ConsolePane.Clear()

```

### EnsureVisible(int lineNumber)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Scorre l'editor in modo che la riga che corrisponde al valore del parametro **lineNumber** specificato sia visibile. Genera un'eccezione se il numero di riga specificato non è compreso nell'intervallo tra 1 e l'ultimo numero di riga, che definisce i numeri di riga validi.

 **lineNumber**
 Numero della riga che deve essere reso visibile.

```
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psIse.CurrentFile.Editor.EnsureVisible(5)

```

### Focus()
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Imposta lo stato attivo nell'editor.

```
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### GetLineLength(int lineNumber)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Ottiene la lunghezza della riga specificata dal numero di riga come valore intero.

 **lineNumber**
 Numero della riga di cui ottenere la lunghezza.

 **Returns**
 La lunghezza della riga per il numero di riga specificato.

```
# Gets the length of the first line in the text of the Command pane. 
$psIse.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### GoToMatch()
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Sposta il cursore sul carattere corrispondente se la proprietà **CanGoToMatch** dell'oggetto editor è **$true**, che si verifica quando il cursore si trova immediatamente prima di una parentesi, di una parentesi quadra o di una parentesi graffa di apertura, (, [, {, o immediatamente dopo una parentesi, di una parentesi quadra o di una parentesi graffa di chiusura, ), ], }.  Il cursore viene posizionato prima di un carattere di apertura o dopo un carattere di chiusura. Se la proprietà **CanGoToMatch** è **$false**, questo metodo non esegue alcuna operazione. Vedere [CanGoToMatch](#cangotomatch)..

```
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### InsertText(text)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Sostituisce la selezione con un testo o inserisce il testo nella posizione corrente del cursore.

 **text**- String
 Il testo da inserire.

 Vedere [Esempio di script](#example) più avanti in questo argomento.

### Select(startLine, startColumn, endLine, endColumn)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Seleziona il testo dai parametri **startLine**, **startColumn**, **endLine** ed **endColumn**.

 **startLine**- Integer
 La riga in cui inizia la selezione.

 **startColumn**- Integer
 La colonna all'interno della riga di inizio in cui inizia la selezione.

 **endLine**- Integer
 La riga in cui termina la selezione.

 **endColumn**- Integer
 La colonna all'interno della riga finale in cui termina la selezione.

 Vedere [Esempio di script](#example) più avanti in questo argomento.

### SelectCaretLine()
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Seleziona l'intera riga di testo che contiene attualmente il cursore.

```
# First, set the caret position on line 5.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psIse.CurrentFile.Editor.SelectCaretLine()

```

### SetCaretPosition(lineNumber, columnNumber)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Imposta la posizione del cursore sul numero di riga e sul numero di colonna. Genera un'eccezione se il numero di riga del cursore o il numero di colonna del cursore non è compreso nei relativi intervalli validi.

 **lineNumber**- Integer
 Il numero di riga del cursore.

 **columnNumber**- Integer
 Il numero di colonna del cursore.

```
# Set the CaretPosition.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1)
```

### ToggleOutliningExpansion()
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Espande o comprime tutte le sezioni della struttura.

```
# Toggle the outlining expansion
$psIse.CurrentFile.Editor.ToggleOutliningExpansion()

```

## Proprietà

###  <a name="CanGoToMatch"></a> CanGoToMatch
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di sola lettura booleana che indica se il cursore è accanto a una parentesi, a una parentesi quadra o a una parentesi graffa (), [], {}. Se il cursore si trova immediatamente prima del carattere di apertura o immediatamente dopo il carattere di chiusura di una coppia, il valore di questa proprietà è **$true**. In caso contrario, è **$false**..

```
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psIse.CurrentFile.Editor.CanGoToMatch

```

###  <a name="CaretColumn"></a> CaretColumn
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il numero di colonna che corrisponde alla posizione del cursore.

```
# Get the CaretColumn.
$psIse.CurrentFile.Editor.CaretColumn

```

###  <a name="CaretLine"></a> CaretLine
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il numero di riga che contiene il cursore.

```
# Get the CaretLine.
$psIse.CurrentFile.Editor.CaretLine

```

###  <a name="caretlinetext"></a> CaretLineText
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene la riga completa che contiene il cursore.

```
# Get all of the text on the line that contains the caret.
$psIse.CurrentFile.Editor.CaretLineText

```

###  <a name="LineCount"></a> LineCount
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il conteggio delle righe dall'editor.

```
# Get the LineCount.
$psIse.CurrentFile.Editor.LineCount

```

###  <a name="SelectedText"></a> SelectedText
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il testo selezionato dall'editor.

 Vedere [Esempio di script](#example) più avanti in questo argomento.

###  <a name="Text"></a> Testo
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per i file.

 Vedere [Esempio di script](#example) più avanti in questo argomento.

##  <a name="example"></a> Esempio di script

```

# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor=$psIse.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## Vedere anche
 [Oggetto ISEFile](The-ISEFile-Object.md) 
 [Oggetto PowerShellTab](The-PowerShellTab-Object.md) 
 [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


