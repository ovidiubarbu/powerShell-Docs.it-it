---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISEOptions
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736948"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="f29b9-103">Oggetto ISEOptions</span><span class="sxs-lookup"><span data-stu-id="f29b9-103">The ISEOptions Object</span></span>

<span data-ttu-id="f29b9-104">L'oggetto **ISEOptions** rappresenta varie impostazioni per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="f29b9-105">È un'istanza della classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="f29b9-106">L'oggetto **ISEOptions** fornisce i metodi e le proprietà seguenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="f29b9-107">Metodi</span><span class="sxs-lookup"><span data-stu-id="f29b9-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="f29b9-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="f29b9-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="f29b9-109">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-110">Ripristina i valori predefiniti dei colori dei token nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="f29b9-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="f29b9-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="f29b9-112">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-113">Ripristina i valori predefiniti di tutte le impostazioni delle opzioni nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="f29b9-114">Reimposta anche il comportamento di vari messaggi di avviso che forniscono la casella di controllo standard per impedire che il messaggio venga visualizzato nuovamente.</span><span class="sxs-lookup"><span data-stu-id="f29b9-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="f29b9-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="f29b9-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="f29b9-116">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-117">Ripristina i valori predefiniti dei colori dei token nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="f29b9-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="f29b9-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="f29b9-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="f29b9-119">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-120">Ripristina i valori predefiniti dei colori dei token per gli elementi XML che vengono visualizzati in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="f29b9-121">Vedere anche [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="f29b9-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="f29b9-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="f29b9-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="f29b9-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="f29b9-124">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-125">Specifica il numero di minuti tra le operazioni di salvataggio automatico dei file con Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="f29b9-126">Il valore predefinito è 2 minuti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-126">The default value is 2 minutes.</span></span> <span data-ttu-id="f29b9-127">Il valore è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="f29b9-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="f29b9-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="f29b9-129">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f29b9-130">Per le versioni successive, vedere [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f29b9-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="f29b9-131">Specifica il colore di sfondo per il riquadro dei comandi.</span><span class="sxs-lookup"><span data-stu-id="f29b9-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="f29b9-132">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="f29b9-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="f29b9-133">CommandPaneUp</span></span>

<span data-ttu-id="f29b9-134">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="f29b9-135">Specifica se il riquadro dei comandi si trova sopra il riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="f29b9-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="f29b9-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="f29b9-137">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-138">Specifica il colore di sfondo per il riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="f29b9-139">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="f29b9-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="f29b9-141">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-142">Specifica il colore primo piano del testo nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="f29b9-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="f29b9-144">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-145">Specifica il colore di sfondo del testo nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="f29b9-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="f29b9-146">ConsoleTokenColors</span></span>

<span data-ttu-id="f29b9-147">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-148">Specifica i colori dei token di IntelliSense nel riquadro della console di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="f29b9-149">Questa proprietà è un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="f29b9-150">Per modificare i colori dei token di IntelliSense nel riquadro di script, vedere [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span>
<span data-ttu-id="f29b9-151">Per reimpostare i colori ai valori predefiniti, vedere [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span>
<span data-ttu-id="f29b9-152">È possibile impostare i colori dei token per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="f29b9-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="f29b9-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-153">DebugBackgroundColor</span></span>

<span data-ttu-id="f29b9-154">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-155">Specifica il colore di sfondo del testo di debug visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-156">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="f29b9-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-157">DebugForegroundColor</span></span>

<span data-ttu-id="f29b9-158">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-159">Specifica il colore primo piano del testo di debug visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-160">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="f29b9-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="f29b9-161">DefaultOptions</span></span>

<span data-ttu-id="f29b9-162">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-163">Raccolta di proprietà che specificano i valori predefiniti da usare quando vengono usati i metodi di reimpostazione.</span><span class="sxs-lookup"><span data-stu-id="f29b9-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a><span data-ttu-id="f29b9-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="f29b9-165">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-166">Specifica il colore di sfondo del testo di errore visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-167">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="f29b9-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-168">ErrorForegroundColor</span></span>

<span data-ttu-id="f29b9-169">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-170">Specifica il colore primo piano del testo di errore visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-171">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="f29b9-172">FontName</span><span class="sxs-lookup"><span data-stu-id="f29b9-172">FontName</span></span>

<span data-ttu-id="f29b9-173">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-174">Specifica il nome del tipo di carattere attualmente in uso nel riquadro di script e nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="f29b9-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="f29b9-175">FontSize</span></span>

<span data-ttu-id="f29b9-176">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-177">Specifica le dimensioni del carattere come numero intero.</span><span class="sxs-lookup"><span data-stu-id="f29b9-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="f29b9-178">Viene usato nel riquadro di script, nel riquadro dei comandi e nel riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="f29b9-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="f29b9-179">L'intervallo di valori valido è da 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="f29b9-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="f29b9-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="f29b9-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="f29b9-181">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-182">Specifica il numero di secondi durante cui IntelliSense prova a risolvere il testo attualmente digitato.</span><span class="sxs-lookup"><span data-stu-id="f29b9-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span>
<span data-ttu-id="f29b9-183">Dopo questo intervallo, IntelliSense raggiunge il timeout e consente di continuare la digitazione.</span><span class="sxs-lookup"><span data-stu-id="f29b9-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="f29b9-184">Il valore predefinito è 3 secondi.</span><span class="sxs-lookup"><span data-stu-id="f29b9-184">The default value is 3 seconds.</span></span> <span data-ttu-id="f29b9-185">Il valore è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="f29b9-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="f29b9-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="f29b9-186">MruCount</span></span>

<span data-ttu-id="f29b9-187">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-188">Specifica il numero di file aperti di recente che Windows PowerShell ISE registra e visualizza alla fine del menu **Apri**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="f29b9-189">Il valore predefinito è 10.</span><span class="sxs-lookup"><span data-stu-id="f29b9-189">The default value is 10.</span></span> <span data-ttu-id="f29b9-190">Il valore è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="f29b9-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="f29b9-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="f29b9-192">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f29b9-193">Per le versioni successive, vedere [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f29b9-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="f29b9-194">Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per il riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="f29b9-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="f29b9-195">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="f29b9-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="f29b9-197">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f29b9-198">Per le versioni successive, vedere [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f29b9-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="f29b9-199">Proprietà di lettura/scrittura che modifica il colore di primo piano del testo nel riquadro di output in Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="f29b9-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="f29b9-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="f29b9-201">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f29b9-202">Per le versioni successive, vedere [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="f29b9-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="f29b9-203">Proprietà di lettura/scrittura che modifica il colore di sfondo del testo nel riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="f29b9-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="f29b9-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="f29b9-205">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-206">Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per i file.</span><span class="sxs-lookup"><span data-stu-id="f29b9-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="f29b9-207">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="f29b9-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="f29b9-209">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-210">Proprietà di lettura/scrittura che ottiene o imposta il colore primo piano per i file non di script nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="f29b9-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="f29b9-211">Per impostare il colore primo piano per i file di script, usare [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="f29b9-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="f29b9-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="f29b9-213">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-214">Proprietà di lettura/scrittura che ottiene o imposta la posizione del riquadro di script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f29b9-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="f29b9-215">La stringa può essere "Maximized", "Top" o "Right".</span><span class="sxs-lookup"><span data-stu-id="f29b9-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="f29b9-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="f29b9-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="f29b9-217">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-218">Specifica se l'elenco di frammenti di codice <kbd>CTRL</kbd>+<kbd>J</kbd> comprende il set iniziale incluso in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f29b9-218">Specifies whether the <kbd>CTRL</kbd>+<kbd>J</kbd> list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="f29b9-219">Se è impostato su `$false`, l'elenco <kbd>CTRL</kbd>+<kbd>J</kbd> includerà solo i frammenti di codice definiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="f29b9-219">When set to `$false`, only user-defined snippets appear in the <kbd>CTRL</kbd>+<kbd>J</kbd> list.</span></span>
<span data-ttu-id="f29b9-220">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-220">The default value is `$true`.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="f29b9-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="f29b9-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="f29b9-222">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-223">Specifica se IntelliSense offre suggerimenti relativi a sintassi, parametri e valori nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span>
<span data-ttu-id="f29b9-224">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-224">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="f29b9-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="f29b9-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="f29b9-226">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-227">Specifica se IntelliSense offre suggerimenti relativi a sintassi, parametri e valori nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="f29b9-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span>
<span data-ttu-id="f29b9-228">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-228">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="f29b9-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="f29b9-229">ShowLineNumbers</span></span>

<span data-ttu-id="f29b9-230">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-231">Specifica se il riquadro di script visualizza i numeri di riga nel margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="f29b9-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="f29b9-232">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-232">The default value is `$true`.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="f29b9-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="f29b9-233">ShowOutlining</span></span>

<span data-ttu-id="f29b9-234">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-235">Specifica se il riquadro di script visualizza le parentesi espandibili e comprimibili accanto alle sezioni di codice nel margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="f29b9-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="f29b9-236">Quando sono visualizzate, è possibile fare clic sull'icona del segno meno (`-`) accanto a un blocco di testo per comprimerlo o sull'icona del segno più (`+`) per espanderlo.</span><span class="sxs-lookup"><span data-stu-id="f29b9-236">When they are displayed, you can click the minus `-` icons next to a block of text to collapse it or click the plus `+` icon to expand a block of text.</span></span> <span data-ttu-id="f29b9-237">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-237">The default value is `$true`.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="f29b9-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="f29b9-238">ShowToolBar</span></span>

<span data-ttu-id="f29b9-239">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-240">Specifica se la barra degli strumenti ISE viene visualizzata nella parte superiore della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="f29b9-241">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-241">The default value is `$true`.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="f29b9-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="f29b9-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="f29b9-243">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-244">Specifica se viene visualizzato un messaggio di avviso quando uno script viene salvato automaticamente prima di essere eseguito.</span><span class="sxs-lookup"><span data-stu-id="f29b9-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span>
<span data-ttu-id="f29b9-245">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-245">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="f29b9-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="f29b9-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="f29b9-247">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-248">Specifica se viene visualizzato un messaggio di avviso quando lo stesso file viene aperto in diverse schede di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f29b9-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="f29b9-249">Se impostato su `$true`, l'apertura dello stesso file in più schede determina la visualizzazione di questo messaggio: "Una copia del file è aperta in un'altra scheda di PowerShell. Le modifiche apportate al file interesseranno tutte le copie aperte".</span><span class="sxs-lookup"><span data-stu-id="f29b9-249">If set to `$true`, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="f29b9-250">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-250">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="f29b9-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="f29b9-251">TokenColors</span></span>

<span data-ttu-id="f29b9-252">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-253">Specifica i colori dei token di IntelliSense nel riquadro di script di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="f29b9-254">Questa proprietà è un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="f29b9-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="f29b9-255">Per modificare i colori dei token di IntelliSense nel riquadro della console, vedere [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span>
<span data-ttu-id="f29b9-256">Per reimpostare i colori ai valori predefiniti, vedere [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span>
<span data-ttu-id="f29b9-257">È possibile impostare i colori dei token per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="f29b9-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="f29b9-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="f29b9-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="f29b9-259">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-260">Specifica se è possibile usare INVIO per selezionare un'opzione fornita da IntelliSense nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="f29b9-261">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-261">The default value is `$true`.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="f29b9-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="f29b9-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="f29b9-263">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-264">Specifica se è possibile usare INVIO per selezionare un'opzione fornita da IntelliSense nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="f29b9-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="f29b9-265">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-265">The default value is `$true`.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="f29b9-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="f29b9-266">UseLocalHelp</span></span>

<span data-ttu-id="f29b9-267">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-268">Specifica se viene visualizzata la Guida installata in locale o la Guida della libreria TechNet online quando si preme <kbd>F1</kbd> con il cursore posizionato su una parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f29b9-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press <kbd>F1</kbd> with the cursor positioned in a keyword.</span></span> <span data-ttu-id="f29b9-269">Se impostato su `$true`, una finestra popup visualizza il contenuto della Guida installata in locale.</span><span class="sxs-lookup"><span data-stu-id="f29b9-269">If set to `$true`, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="f29b9-270">È possibile installare i file della Guida con il comando `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="f29b9-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="f29b9-271">Se impostato su `$false`, il browser apre una pagina della libreria TechNet.</span><span class="sxs-lookup"><span data-stu-id="f29b9-271">If set to `$false`, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="f29b9-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="f29b9-273">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-274">Specifica il colore di sfondo del testo dettagliato visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-275">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="f29b9-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-276">VerboseForegroundColor</span></span>

<span data-ttu-id="f29b9-277">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-278">Specifica il colore primo piano del testo dettagliato visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-279">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="f29b9-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-280">WarningBackgroundColor</span></span>

<span data-ttu-id="f29b9-281">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-282">Specifica il colore di sfondo del testo di avviso visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="f29b9-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="f29b9-283">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="f29b9-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="f29b9-284">WarningForegroundColor</span></span>

<span data-ttu-id="f29b9-285">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f29b9-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f29b9-286">Specifica il colore primo piano del testo di avviso visualizzato nel riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="f29b9-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="f29b9-287">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="f29b9-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="f29b9-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="f29b9-288">XmlTokenColors</span></span>

<span data-ttu-id="f29b9-289">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-290">Specifica un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il contenuto XML visualizzato in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f29b9-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="f29b9-291">È possibile impostare i colori dei token per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="f29b9-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="f29b9-292">Vedere anche [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="f29b9-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="f29b9-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="f29b9-293">Zoom</span></span>

<span data-ttu-id="f29b9-294">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f29b9-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f29b9-295">Specifica le dimensioni relative del testo nei riquadri della console e di script.</span><span class="sxs-lookup"><span data-stu-id="f29b9-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="f29b9-296">Il valore predefinito è 100.</span><span class="sxs-lookup"><span data-stu-id="f29b9-296">The default value is 100.</span></span>
<span data-ttu-id="f29b9-297">Se si specificano valori inferiori o superiori, il testo in Windows PowerShell ISE risulta rimpicciolito o ingrandito.</span><span class="sxs-lookup"><span data-stu-id="f29b9-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="f29b9-298">Il valore è un numero intero compreso tra 20 e 400.</span><span class="sxs-lookup"><span data-stu-id="f29b9-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="f29b9-299">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f29b9-299">See Also</span></span>

- [<span data-ttu-id="f29b9-300">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f29b9-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f29b9-301">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="f29b9-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
