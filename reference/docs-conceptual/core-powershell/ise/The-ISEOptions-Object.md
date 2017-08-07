---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="ce9be-103">Oggetto ISEOptions</span><span class="sxs-lookup"><span data-stu-id="ce9be-103">The ISEOptions Object</span></span>
  <span data-ttu-id="ce9be-104">L'oggetto **ISEOptions** rappresenta varie impostazioni per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="ce9be-105">È un'istanza della classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="ce9be-106">L'oggetto **ISEOptions** fornisce i metodi e le proprietà seguenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="ce9be-107">**Metodi**</span><span class="sxs-lookup"><span data-stu-id="ce9be-107">**Methods**</span></span>

-   [<span data-ttu-id="ce9be-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="ce9be-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="ce9be-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="ce9be-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="ce9be-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="ce9be-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="ce9be-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="ce9be-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="ce9be-112">**Proprietà**</span><span class="sxs-lookup"><span data-stu-id="ce9be-112">**Properties**</span></span>

-   [<span data-ttu-id="ce9be-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="ce9be-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="ce9be-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="ce9be-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="ce9be-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="ce9be-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="ce9be-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="ce9be-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="ce9be-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="ce9be-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="ce9be-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="ce9be-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="ce9be-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="ce9be-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="ce9be-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="ce9be-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="ce9be-125">FontName</span><span class="sxs-lookup"><span data-stu-id="ce9be-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="ce9be-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="ce9be-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="ce9be-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="ce9be-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="ce9be-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="ce9be-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="ce9be-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="ce9be-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="ce9be-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="ce9be-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="ce9be-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="ce9be-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="ce9be-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="ce9be-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="ce9be-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="ce9be-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="ce9be-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="ce9be-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="ce9be-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="ce9be-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="ce9be-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="ce9be-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="ce9be-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="ce9be-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="ce9be-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="ce9be-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="ce9be-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="ce9be-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="ce9be-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="ce9be-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="ce9be-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="ce9be-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="ce9be-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="ce9be-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="ce9be-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="ce9be-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="ce9be-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="ce9be-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="ce9be-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="ce9be-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="ce9be-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="ce9be-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="ce9be-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="ce9be-152">Zoom</span><span class="sxs-lookup"><span data-stu-id="ce9be-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="ce9be-153">Metodo</span><span class="sxs-lookup"><span data-stu-id="ce9be-153">Methods</span></span>

###  <span data-ttu-id="ce9be-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="ce9be-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="ce9be-155">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-156">Ripristina i valori predefiniti dei colori dei token nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="ce9be-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="ce9be-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="ce9be-158">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-159">Ripristina i valori predefiniti di tutte le impostazioni delle opzioni nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="ce9be-160">Reimposta anche il comportamento di vari messaggi di avviso che forniscono la casella di controllo standard per impedire che il messaggio venga visualizzato nuovamente.</span><span class="sxs-lookup"><span data-stu-id="ce9be-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="ce9be-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="ce9be-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="ce9be-162">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-163">Ripristina i valori predefiniti dei colori dei token nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="ce9be-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="ce9be-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="ce9be-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="ce9be-165">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-166">Ripristina i valori predefiniti dei colori dei token per gli elementi XML che vengono visualizzati in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="ce9be-167">Vedere anche [XmlTokenColors](#xtc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="ce9be-168">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ce9be-168">Properties</span></span>

###  <span data-ttu-id="ce9be-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="ce9be-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="ce9be-170">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-171">Specifica il numero di minuti tra le operazioni di salvataggio automatico dei file con Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="ce9be-172">Il valore predefinito è 2 minuti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-172">The default value is 2 minutes.</span></span> <span data-ttu-id="ce9be-173">Il valore è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="ce9be-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="ce9be-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="ce9be-175">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="ce9be-176">Per le versioni successive, vedere [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="ce9be-177">Specifica il colore di sfondo per il riquadro dei comandi.</span><span class="sxs-lookup"><span data-stu-id="ce9be-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="ce9be-178">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="ce9be-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="ce9be-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="ce9be-180">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="ce9be-181">Specifica se il riquadro dei comandi si trova sopra il riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="ce9be-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="ce9be-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="ce9be-183">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-184">Specifica il colore di sfondo per il riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="ce9be-185">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="ce9be-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="ce9be-187">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-188">Specifica il colore primo piano del testo nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="ce9be-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="ce9be-190">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-191">Specifica il colore di sfondo del testo nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="ce9be-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="ce9be-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="ce9be-193">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-194">Specifica i colori dei token di IntelliSense nel riquadro della console di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="ce9be-195">Questa proprietà è un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="ce9be-196">Per modificare i colori dei token di IntelliSense nel riquadro di script, vedere [TokenColors](#tc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="ce9be-197">Per reimpostare i colori ai valori predefiniti, vedere [RestoreDefaultConsoleTokenColors()](#rdctc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="ce9be-198">I colori dei token possono essere impostati per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="ce9be-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="ce9be-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="ce9be-200">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-201">Specifica il colore di sfondo del testo di debug visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-202">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="ce9be-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="ce9be-204">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-205">Specifica il colore primo piano del testo di debug visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-206">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="ce9be-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="ce9be-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="ce9be-208">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-209">Raccolta di proprietà che specificano i valori predefiniti da usare quando vengono usati i metodi di reimpostazione.</span><span class="sxs-lookup"><span data-stu-id="ce9be-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

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

###  <span data-ttu-id="ce9be-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="ce9be-211">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-212">Specifica il colore di sfondo del testo di errore visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-213">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="ce9be-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="ce9be-215">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-216">Specifica il colore primo piano del testo di errore visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-217">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="ce9be-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="ce9be-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="ce9be-219">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-220">Specifica il nome del tipo di carattere attualmente in uso nel riquadro di script e nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="ce9be-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="ce9be-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="ce9be-222">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-223">Specifica le dimensioni del carattere come numero intero.</span><span class="sxs-lookup"><span data-stu-id="ce9be-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="ce9be-224">Viene usato nel riquadro di script, nel riquadro dei comandi e nel riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="ce9be-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="ce9be-225">L'intervallo di valori valido è da 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="ce9be-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="ce9be-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="ce9be-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="ce9be-227">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-228">Specifica il numero di secondi durante cui IntelliSense prova a risolvere il testo attualmente digitato.</span><span class="sxs-lookup"><span data-stu-id="ce9be-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="ce9be-229">Dopo questo intervallo, IntelliSense raggiunge il timeout e consente di continuare la digitazione.</span><span class="sxs-lookup"><span data-stu-id="ce9be-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="ce9be-230">Il valore predefinito è 3 secondi.</span><span class="sxs-lookup"><span data-stu-id="ce9be-230">The default value is 3 seconds.</span></span> <span data-ttu-id="ce9be-231">Il valore è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="ce9be-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="ce9be-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="ce9be-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="ce9be-233">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-234">Specifica il numero di file aperti di recente che Windows PowerShell ISE registra e visualizza alla fine del menu **Apri**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="ce9be-235">Il valore predefinito è 10.</span><span class="sxs-lookup"><span data-stu-id="ce9be-235">The default value is 10.</span></span> <span data-ttu-id="ce9be-236">Il valore è un numero intero.</span><span class="sxs-lookup"><span data-stu-id="ce9be-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="ce9be-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="ce9be-238">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="ce9be-239">Per le versioni successive, vedere [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="ce9be-240">Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per il riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="ce9be-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="ce9be-241">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="ce9be-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="ce9be-243">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="ce9be-244">Per le versioni successive, vedere [ConsolePaneForegroundColor](#conpfc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="ce9be-245">Proprietà di lettura/scrittura che modifica il colore di primo piano del testo nel riquadro di output in Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="ce9be-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="ce9be-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="ce9be-247">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="ce9be-248">Per le versioni successive, vedere [ConsolePaneTextBackgroundColor](#conptbc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="ce9be-249">Proprietà di lettura/scrittura che modifica il colore di sfondo del testo nel riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="ce9be-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="ce9be-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="ce9be-251">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-252">Proprietà di lettura/scrittura che ottiene o imposta il colore di sfondo per i file.</span><span class="sxs-lookup"><span data-stu-id="ce9be-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="ce9be-253">È un'istanza della classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="ce9be-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="ce9be-255">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-256">Proprietà di lettura/scrittura che ottiene o imposta il colore primo piano per i file non di script nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="ce9be-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="ce9be-257">Per impostare il colore primo piano per i file di script, usare la proprietà [TokenColors](The-ISEOptions-Object.md#tc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="ce9be-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="ce9be-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="ce9be-259">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-260">Proprietà di lettura/scrittura che ottiene o imposta la posizione del riquadro di script nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ce9be-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="ce9be-261">La stringa può essere "Maximized", "Top" o "Right".</span><span class="sxs-lookup"><span data-stu-id="ce9be-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="ce9be-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="ce9be-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="ce9be-263">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-264">Specifica se l'elenco di frammenti di codice di **CTRL+J** comprende il set iniziale incluso in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce9be-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="ce9be-265">Se è impostato su **$false**, vengono visualizzati solo i frammenti di codice definiti dall'utente nell'elenco **CTRL+J**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="ce9be-266">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="ce9be-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="ce9be-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="ce9be-268">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-269">Specifica se IntelliSense offre suggerimenti relativi a sintassi, parametri e valori nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="ce9be-270">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="ce9be-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="ce9be-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="ce9be-272">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-273">Specifica se IntelliSense offre suggerimenti relativi a sintassi, parametri e valori nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="ce9be-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="ce9be-274">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="ce9be-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="ce9be-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="ce9be-276">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-277">Specifica se il riquadro di script visualizza i numeri di riga nel margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="ce9be-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="ce9be-278">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="ce9be-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="ce9be-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="ce9be-280">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-281">Specifica se il riquadro di script visualizza le parentesi espandibili e comprimibili accanto alle sezioni di codice nel margine sinistro.</span><span class="sxs-lookup"><span data-stu-id="ce9be-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="ce9be-282">Quando sono visualizzate, è possibile fare clic sull'icona del segno meno \(-\) accanto a un blocco di testo per comprimerlo o sull'icona del segno più \(+\) per espanderlo.</span><span class="sxs-lookup"><span data-stu-id="ce9be-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="ce9be-283">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="ce9be-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="ce9be-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="ce9be-285">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-286">Specifica se la barra degli strumenti ISE viene visualizzata nella parte superiore della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="ce9be-287">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="ce9be-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="ce9be-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="ce9be-289">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-290">Specifica se viene visualizzato un messaggio di avviso quando uno script viene salvato automaticamente prima di essere eseguito.</span><span class="sxs-lookup"><span data-stu-id="ce9be-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="ce9be-291">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="ce9be-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="ce9be-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="ce9be-293">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-294">Specifica se viene visualizzato un messaggio di avviso quando lo stesso file viene aperto in diverse schede di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce9be-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="ce9be-295">Se è impostato su **$true**, quando si apre lo stesso file in più schede, viene visualizzato il messaggio: "Una copia del file è aperta in un'altra scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce9be-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="ce9be-296">Le modifiche apportate al file interesseranno tutte le copie aperte".</span><span class="sxs-lookup"><span data-stu-id="ce9be-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="ce9be-297">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="ce9be-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="ce9be-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="ce9be-299">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-300">Specifica i colori dei token di IntelliSense nel riquadro di script di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="ce9be-301">Questa proprietà è un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="ce9be-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="ce9be-302">Per modificare i colori dei token di IntelliSense nel riquadro della console, vedere [ConsoleTokenColors](#contc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="ce9be-303">Per reimpostare i colori ai valori predefiniti, vedere [RestoreDefaultTokenColors()](#rdtc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="ce9be-304">I colori dei token possono essere impostati per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="ce9be-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="ce9be-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="ce9be-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="ce9be-306">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-307">Specifica se è possibile usare INVIO per selezionare un'opzione fornita da IntelliSense nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="ce9be-308">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="ce9be-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="ce9be-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="ce9be-310">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-311">Specifica se è possibile usare INVIO per selezionare un'opzione fornita da IntelliSense nel riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="ce9be-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="ce9be-312">Il valore predefinito è **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="ce9be-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="ce9be-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="ce9be-314">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-315">Specifica se la Guida installata in locale o la Guida della libreria TechNet online viene visualizzata quando si preme F1 con il cursore posizionato su una parola chiave.</span><span class="sxs-lookup"><span data-stu-id="ce9be-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="ce9be-316">Se è impostato su **$true**, una finestra popup visualizza il contenuto della Guida installata in locale.</span><span class="sxs-lookup"><span data-stu-id="ce9be-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="ce9be-317">È possibile installare i file della Guida con il comando `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="ce9be-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="ce9be-318">Se è impostato su **$false**, il browser apre una pagina della libreria TechNet.</span><span class="sxs-lookup"><span data-stu-id="ce9be-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="ce9be-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="ce9be-320">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-321">Specifica il colore di sfondo del testo dettagliato visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-322">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="ce9be-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="ce9be-324">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-325">Specifica il colore primo piano del testo dettagliato visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-326">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="ce9be-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="ce9be-328">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-329">Specifica il colore di sfondo del testo di avviso visualizzato nel riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="ce9be-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="ce9be-330">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="ce9be-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ce9be-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="ce9be-332">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ce9be-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ce9be-333">Specifica il colore primo piano del testo di avviso visualizzato nel riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="ce9be-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="ce9be-334">È un oggetto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="ce9be-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="ce9be-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="ce9be-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="ce9be-336">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-337">Specifica un oggetto dizionario che contiene le coppie nome/valore dei tipi e dei colori dei token per il contenuto XML visualizzato in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ce9be-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="ce9be-338">I colori dei token possono essere impostati per gli elementi seguenti: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="ce9be-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="ce9be-339">Vedere anche [RestoreDefaultXmlTokenColors()](#rdxtc).</span><span class="sxs-lookup"><span data-stu-id="ce9be-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="ce9be-340"><a name="z"></a> Zoom</span><span class="sxs-lookup"><span data-stu-id="ce9be-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="ce9be-341">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="ce9be-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="ce9be-342">Specifica le dimensioni relative del testo nei riquadri della console e di script.</span><span class="sxs-lookup"><span data-stu-id="ce9be-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="ce9be-343">Il valore predefinito è 100.</span><span class="sxs-lookup"><span data-stu-id="ce9be-343">The default value is 100.</span></span> <span data-ttu-id="ce9be-344">Se si specificano valori inferiori o superiori, il testo in Windows PowerShell ISE risulta rimpicciolito o ingrandito.</span><span class="sxs-lookup"><span data-stu-id="ce9be-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="ce9be-345">Il valore è un numero intero compreso tra 20 e 400.</span><span class="sxs-lookup"><span data-stu-id="ce9be-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="ce9be-346">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ce9be-346">See Also</span></span>
- [<span data-ttu-id="ce9be-347">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ce9be-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ce9be-348">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ce9be-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

