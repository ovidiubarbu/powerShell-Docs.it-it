---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEEditor
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
ms.openlocfilehash: 41f2a6f7684275ad9d6d967ea67b64ca02c1c100
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="eb243-103">Oggetto ISEEditor</span><span class="sxs-lookup"><span data-stu-id="eb243-103">The ISEEditor Object</span></span>
  <span data-ttu-id="eb243-104">Un oggetto **ISEEditor** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="eb243-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="eb243-105">Il riquadro della console è un oggetto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="eb243-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="eb243-106">Ogni oggetto [ISEFile](The-ISEFile-Object.md) ha un oggetto **ISEEditor** associato.</span><span class="sxs-lookup"><span data-stu-id="eb243-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="eb243-107">Le sezioni seguenti elencano i metodi e proprietà di un oggetto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="eb243-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="eb243-108">Metodo</span><span class="sxs-lookup"><span data-stu-id="eb243-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="eb243-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="eb243-109">Clear\(\)</span></span>
  <span data-ttu-id="eb243-110">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-111">Cancella il testo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="eb243-111">Clears the text in the editor.</span></span>

```PowerShell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="eb243-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="eb243-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="eb243-113">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-114">Scorre l'editor in modo che la riga che corrisponde al valore del parametro **lineNumber** specificato sia visibile.</span><span class="sxs-lookup"><span data-stu-id="eb243-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="eb243-115">Genera un'eccezione se il numero di riga specificato non è compreso nell'intervallo tra 1 e l'ultimo numero di riga, che definisce i numeri di riga validi.</span><span class="sxs-lookup"><span data-stu-id="eb243-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="eb243-116">**lineNumber**
 Numero della riga che deve essere reso visibile.</span><span class="sxs-lookup"><span data-stu-id="eb243-116">**lineNumber**
 The number of the line that is to be made visible.</span></span>

```PowerShell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="eb243-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="eb243-117">Focus\(\)</span></span>
  <span data-ttu-id="eb243-118">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-119">Imposta lo stato attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="eb243-119">Sets the focus to the editor.</span></span>

```PowerShell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="eb243-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="eb243-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="eb243-121">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-122">Ottiene la lunghezza della riga specificata dal numero di riga come valore intero.</span><span class="sxs-lookup"><span data-stu-id="eb243-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="eb243-123">**lineNumber**
 Numero della riga di cui ottenere la lunghezza.</span><span class="sxs-lookup"><span data-stu-id="eb243-123">**lineNumber**
 The number of the line of which to get the length.</span></span>

 <span data-ttu-id="eb243-124">**Returns**
 Lunghezza della riga per il numero di riga specificato.</span><span class="sxs-lookup"><span data-stu-id="eb243-124">**Returns**
 The line length for the line at the specified line number.</span></span>

```PowerShell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="eb243-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="eb243-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="eb243-126">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="eb243-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="eb243-127">Sposta il cursore sul carattere corrispondente se la proprietà **CanGoToMatch** dell'oggetto editor è **$true**, il che si verifica quando il cursore si trova immediatamente prima di una parentesi, di una parentesi quadra o di una parentesi graffa di apertura, \(, \[, { o immediatamente dopo una parentesi, una parentesi quadra o una parentesi graffa di chiusura, \), \], }.</span><span class="sxs-lookup"><span data-stu-id="eb243-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="eb243-128">Il cursore viene posizionato prima di un carattere di apertura o dopo un carattere di chiusura.</span><span class="sxs-lookup"><span data-stu-id="eb243-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="eb243-129">Se la proprietà **CanGoToMatch** è **$false**, questo metodo non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="eb243-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span> <span data-ttu-id="eb243-130">Vedere [CanGoToMatch](#cangotomatch).</span><span class="sxs-lookup"><span data-stu-id="eb243-130">See [CanGoToMatch](#cangotomatch).</span></span>

```PowerShell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="eb243-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="eb243-131">InsertText\( text \)</span></span>
  <span data-ttu-id="eb243-132">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-133">Sostituisce la selezione con un testo o inserisce il testo nella posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="eb243-134">**text** - Stringa Il testo da inserire.</span><span class="sxs-lookup"><span data-stu-id="eb243-134">**text** - String The text to insert.</span></span>

 <span data-ttu-id="eb243-135">Vedere [Esempio di script](#example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="eb243-135">See the [Scripting Example](#example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="eb243-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="eb243-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="eb243-137">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-138">Seleziona il testo dai parametri **startLine**, **startColumn**, **endLine** ed **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="eb243-138">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="eb243-139">**startLine** - Intero La riga in cui inizia la selezione.</span><span class="sxs-lookup"><span data-stu-id="eb243-139">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="eb243-140">**startColumn** - Intero La colonna all'interno della riga di inizio in cui inizia la selezione.</span><span class="sxs-lookup"><span data-stu-id="eb243-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="eb243-141">**endLine** - Intero La riga in cui termina la selezione.</span><span class="sxs-lookup"><span data-stu-id="eb243-141">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="eb243-142">**endColumn** - Intero La colonna all'interno della riga di fine in cui termina la selezione.</span><span class="sxs-lookup"><span data-stu-id="eb243-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="eb243-143">Vedere [Esempio di script](#example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="eb243-143">See the  [Scripting Example](#example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="eb243-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="eb243-144">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="eb243-145">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-146">Seleziona l'intera riga di testo che contiene attualmente il cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-146">Selects the entire line of text that currently contains the caret.</span></span>

```PowerShell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="eb243-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="eb243-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="eb243-148">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-149">Imposta la posizione del cursore sul numero di riga e sul numero di colonna.</span><span class="sxs-lookup"><span data-stu-id="eb243-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="eb243-150">Genera un'eccezione se il numero di riga del cursore o il numero di colonna del cursore non è compreso nei relativi intervalli validi.</span><span class="sxs-lookup"><span data-stu-id="eb243-150">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="eb243-151">**lineNumber** - Intero Il numero di riga del cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-151">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="eb243-152">**columnNumber** - Intero Il numero di colonna del cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-152">**columnNumber** - Integer The caret column number.</span></span>

```PowerShell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="eb243-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="eb243-153">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="eb243-154">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="eb243-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="eb243-155">Espande o comprime tutte le sezioni della struttura.</span><span class="sxs-lookup"><span data-stu-id="eb243-155">Causes all the outline sections to expand or collapse.</span></span>

```PowerShell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="eb243-156">Proprietà</span><span class="sxs-lookup"><span data-stu-id="eb243-156">Properties</span></span>

###  <span data-ttu-id="eb243-157"><a name="CanGoToMatch"></a> CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="eb243-157"><a name="CanGoToMatch"></a> CanGoToMatch</span></span>
  <span data-ttu-id="eb243-158">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="eb243-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="eb243-159">Proprietà di sola lettura booleana che indica se il cursore si trova accanto a una parentesi, a una parentesi quadra o a una parentesi graffa - \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="eb243-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="eb243-160">Se il cursore si trova immediatamente prima del carattere di apertura o immediatamente dopo il carattere di chiusura di una coppia, il valore di questa proprietà è **$true**.</span><span class="sxs-lookup"><span data-stu-id="eb243-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="eb243-161">In caso contrario, è **$false**.</span><span class="sxs-lookup"><span data-stu-id="eb243-161">Otherwise, it is **$false**.</span></span>

```PowerShell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <span data-ttu-id="eb243-162"><a name="CaretColumn"></a> CaretColumn</span><span class="sxs-lookup"><span data-stu-id="eb243-162"><a name="CaretColumn"></a> CaretColumn</span></span>
  <span data-ttu-id="eb243-163">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-164">Proprietà di sola lettura che ottiene il numero di colonna che corrisponde alla posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```PowerShell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <span data-ttu-id="eb243-165"><a name="CaretLine"></a> CaretLine</span><span class="sxs-lookup"><span data-stu-id="eb243-165"><a name="CaretLine"></a> CaretLine</span></span>
  <span data-ttu-id="eb243-166">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-167">Proprietà di sola lettura che ottiene il numero di riga che contiene il cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```PowerShell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <span data-ttu-id="eb243-168"><a name="CaretLineText"></a> CaretLineText</span><span class="sxs-lookup"><span data-stu-id="eb243-168"><a name="CaretLineText"></a> CaretLineText</span></span>
  <span data-ttu-id="eb243-169">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-170">Proprietà di sola lettura che ottiene la riga completa che contiene il cursore.</span><span class="sxs-lookup"><span data-stu-id="eb243-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```PowerShell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <span data-ttu-id="eb243-171"><a name="LineCount"></a> LineCount</span><span class="sxs-lookup"><span data-stu-id="eb243-171"><a name="LineCount"></a> LineCount</span></span>
  <span data-ttu-id="eb243-172">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-173">Proprietà di sola lettura che ottiene il conteggio delle righe dall'editor.</span><span class="sxs-lookup"><span data-stu-id="eb243-173">The read-only property that gets the line count from the editor.</span></span>

```PowerShell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <span data-ttu-id="eb243-174"><a name="SelectedText"></a> SelectedText</span><span class="sxs-lookup"><span data-stu-id="eb243-174"><a name="SelectedText"></a> SelectedText</span></span>
  <span data-ttu-id="eb243-175">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-176">Proprietà di sola lettura che ottiene il testo selezionato dall'editor.</span><span class="sxs-lookup"><span data-stu-id="eb243-176">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="eb243-177">Vedere [Esempio di script](#example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="eb243-177">See the  [Scripting Example](#example) later in this topic.</span></span>

###  <span data-ttu-id="eb243-178"><a name="Text"></a> Text</span><span class="sxs-lookup"><span data-stu-id="eb243-178"><a name="Text"></a> Text</span></span>
  <span data-ttu-id="eb243-179">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eb243-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eb243-180">Proprietà di lettura/scrittura che ottiene o imposta il testo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="eb243-180">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="eb243-181">Vedere [Esempio di script](#example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="eb243-181">See the [Scripting Example](#example) later in this topic.</span></span>

##  <span data-ttu-id="eb243-182"><a name="example"></a> Esempio di script</span><span class="sxs-lookup"><span data-stu-id="eb243-182"><a name="example"></a> Scripting Example</span></span>

```PowerShell
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
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="eb243-183">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eb243-183">See Also</span></span>
- [<span data-ttu-id="eb243-184">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="eb243-184">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="eb243-185">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="eb243-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="eb243-186">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eb243-186">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="eb243-187">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eb243-187">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="eb243-188">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="eb243-188">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
