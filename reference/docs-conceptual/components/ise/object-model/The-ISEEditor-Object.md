---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEEditor
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086766"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="c98f6-103">Oggetto ISEEditor</span><span class="sxs-lookup"><span data-stu-id="c98f6-103">The ISEEditor Object</span></span>

<span data-ttu-id="c98f6-104">Un oggetto **ISEEditor** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="c98f6-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="c98f6-105">Il riquadro della console è un oggetto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="c98f6-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="c98f6-106">Ogni oggetto [ISEFile](The-ISEFile-Object.md) ha un oggetto **ISEEditor** associato.</span><span class="sxs-lookup"><span data-stu-id="c98f6-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="c98f6-107">Le sezioni seguenti elencano i metodi e proprietà di un oggetto **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="c98f6-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="c98f6-108">Metodi</span><span class="sxs-lookup"><span data-stu-id="c98f6-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="c98f6-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="c98f6-109">Clear\(\)</span></span>

<span data-ttu-id="c98f6-110">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-111">Cancella il testo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="c98f6-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="c98f6-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="c98f6-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="c98f6-113">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-114">Scorre l'editor in modo che la riga che corrisponde al valore del parametro **lineNumber** specificato sia visibile.</span><span class="sxs-lookup"><span data-stu-id="c98f6-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="c98f6-115">Genera un'eccezione se il numero di riga specificato non è compreso nell'intervallo tra 1 e l'ultimo numero di riga, che definisce i numeri di riga validi.</span><span class="sxs-lookup"><span data-stu-id="c98f6-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="c98f6-116">**lineNumber** Numero della riga che deve essere resa visibile.</span><span class="sxs-lookup"><span data-stu-id="c98f6-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="c98f6-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="c98f6-117">Focus\(\)</span></span>

<span data-ttu-id="c98f6-118">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-119">Imposta lo stato attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="c98f6-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="c98f6-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="c98f6-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="c98f6-121">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-122">Ottiene la lunghezza della riga specificata dal numero di riga come valore intero.</span><span class="sxs-lookup"><span data-stu-id="c98f6-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="c98f6-123">**lineNumber** Numero della riga di cui ottenere la lunghezza.</span><span class="sxs-lookup"><span data-stu-id="c98f6-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="c98f6-124">**Returns** Lunghezza della riga in corrispondenza del numero di riga specificato.</span><span class="sxs-lookup"><span data-stu-id="c98f6-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="c98f6-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="c98f6-125">GoToMatch\(\)</span></span>

<span data-ttu-id="c98f6-126">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="c98f6-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c98f6-127">Sposta il cursore sul carattere corrispondente se la proprietà **CanGoToMatch** dell'oggetto editor è **$true**, il che si verifica quando il cursore si trova immediatamente prima di una parentesi, di una parentesi quadra o di una parentesi graffa di apertura, \(, \[, { o immediatamente dopo una parentesi, una parentesi quadra o una parentesi graffa di chiusura, \), \], }.</span><span class="sxs-lookup"><span data-stu-id="c98f6-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="c98f6-128">Il cursore viene posizionato prima di un carattere di apertura o dopo un carattere di chiusura.</span><span class="sxs-lookup"><span data-stu-id="c98f6-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="c98f6-129">Se la proprietà **CanGoToMatch** è **$false**, questo metodo non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="c98f6-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="c98f6-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="c98f6-130">InsertText\( text \)</span></span>

<span data-ttu-id="c98f6-131">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-132">Sostituisce la selezione con un testo o inserisce il testo nella posizione corrente del cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="c98f6-133">**text** - Stringa Il testo da inserire.</span><span class="sxs-lookup"><span data-stu-id="c98f6-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="c98f6-134">Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="c98f6-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="c98f6-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="c98f6-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="c98f6-136">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-137">Seleziona il testo dai parametri **startLine**, **startColumn**, **endLine** ed **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="c98f6-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="c98f6-138">**startLine** - Intero La riga in cui inizia la selezione.</span><span class="sxs-lookup"><span data-stu-id="c98f6-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="c98f6-139">**startColumn** - Intero La colonna all'interno della riga di inizio in cui inizia la selezione.</span><span class="sxs-lookup"><span data-stu-id="c98f6-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="c98f6-140">**endLine** - Intero La riga in cui termina la selezione.</span><span class="sxs-lookup"><span data-stu-id="c98f6-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="c98f6-141">**endColumn** - Intero La colonna all'interno della riga di fine in cui termina la selezione.</span><span class="sxs-lookup"><span data-stu-id="c98f6-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="c98f6-142">Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="c98f6-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="c98f6-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="c98f6-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="c98f6-144">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-145">Seleziona l'intera riga di testo che contiene attualmente il cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="c98f6-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="c98f6-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="c98f6-147">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-148">Imposta la posizione del cursore sul numero di riga e sul numero di colonna.</span><span class="sxs-lookup"><span data-stu-id="c98f6-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="c98f6-149">Genera un'eccezione se il numero di riga del cursore o il numero di colonna del cursore non è compreso nei relativi intervalli validi.</span><span class="sxs-lookup"><span data-stu-id="c98f6-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="c98f6-150">**lineNumber** - Intero Il numero di riga del cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="c98f6-151">**columnNumber** - Intero Il numero di colonna del cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="c98f6-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="c98f6-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="c98f6-153">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="c98f6-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c98f6-154">Espande o comprime tutte le sezioni della struttura.</span><span class="sxs-lookup"><span data-stu-id="c98f6-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="c98f6-155">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c98f6-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="c98f6-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="c98f6-156">CanGoToMatch</span></span>

<span data-ttu-id="c98f6-157">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="c98f6-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c98f6-158">Proprietà di sola lettura booleana che indica se il cursore si trova accanto a una parentesi, a una parentesi quadra o a una parentesi graffa - \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="c98f6-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="c98f6-159">Se il cursore si trova immediatamente prima del carattere di apertura o immediatamente dopo il carattere di chiusura di una coppia, il valore di questa proprietà è **$true**.</span><span class="sxs-lookup"><span data-stu-id="c98f6-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="c98f6-160">In caso contrario, è **$false**.</span><span class="sxs-lookup"><span data-stu-id="c98f6-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="c98f6-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="c98f6-161">CaretColumn</span></span>

<span data-ttu-id="c98f6-162">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-163">Proprietà di sola lettura che ottiene il numero di colonna che corrisponde alla posizione del cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="c98f6-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="c98f6-164">CaretLine</span></span>

<span data-ttu-id="c98f6-165">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-166">Proprietà di sola lettura che ottiene il numero di riga che contiene il cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="c98f6-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="c98f6-167">CaretLineText</span></span>

<span data-ttu-id="c98f6-168">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-169">Proprietà di sola lettura che ottiene la riga completa che contiene il cursore.</span><span class="sxs-lookup"><span data-stu-id="c98f6-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="c98f6-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="c98f6-170">LineCount</span></span>

<span data-ttu-id="c98f6-171">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-172">Proprietà di sola lettura che ottiene il conteggio delle righe dall'editor.</span><span class="sxs-lookup"><span data-stu-id="c98f6-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="c98f6-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="c98f6-173">SelectedText</span></span>

<span data-ttu-id="c98f6-174">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-175">Proprietà di sola lettura che ottiene il testo selezionato dall'editor.</span><span class="sxs-lookup"><span data-stu-id="c98f6-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="c98f6-176">Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="c98f6-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="c98f6-177">Testo</span><span class="sxs-lookup"><span data-stu-id="c98f6-177">Text</span></span>

<span data-ttu-id="c98f6-178">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c98f6-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c98f6-179">Proprietà di lettura/scrittura che ottiene o imposta il testo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="c98f6-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="c98f6-180">Vedere [Esempio di script](#scripting-example) più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="c98f6-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="c98f6-181">Esempio di script</span><span class="sxs-lookup"><span data-stu-id="c98f6-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c98f6-182">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c98f6-182">See Also</span></span>

- [<span data-ttu-id="c98f6-183">Oggetto ISEFile</span><span class="sxs-lookup"><span data-stu-id="c98f6-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="c98f6-184">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="c98f6-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="c98f6-185">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c98f6-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c98f6-186">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="c98f6-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)