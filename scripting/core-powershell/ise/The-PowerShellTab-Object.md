---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: d4e9374202d352a30b3eb46bcf1e4e40dea49822
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="a2125-103">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="a2125-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="a2125-104">L'oggetto **PowerShellTab** rappresenta un ambiente di runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2125-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="a2125-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="a2125-105">Methods</span></span>

###  <span data-ttu-id="a2125-106"><a name="invoke"></a> Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="a2125-106"><a name="invoke"></a> Invoke\( Script \)</span></span>
  <span data-ttu-id="a2125-107">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-108">Esegue lo script specificato nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2125-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="a2125-109">Questo metodo funziona solo su altre schede di PowerShell, non sulla scheda da cui viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="a2125-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="a2125-110">Non restituisce oggetti o valori.</span><span class="sxs-lookup"><span data-stu-id="a2125-110">It does not return any object or value.</span></span> <span data-ttu-id="a2125-111">Se il codice modifica una variabile, le modifiche vengono mantenute nella scheda in cui è stato richiamato il comando.</span><span class="sxs-lookup"><span data-stu-id="a2125-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="a2125-112">**Script** - System.Management.Automation.ScriptBlock or String Il blocco di script da eseguire.</span><span class="sxs-lookup"><span data-stu-id="a2125-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="a2125-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="a2125-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="a2125-114">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a2125-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="a2125-115">Esegue lo script specificato nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2125-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="a2125-116">Questo metodo funziona solo su altre schede di PowerShell, non sulla scheda da cui viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="a2125-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="a2125-117">Il blocco di script viene eseguito e qualsiasi valore restituito dallo script viene restituito all'ambiente di esecuzione da cui è stato richiamato il comando.</span><span class="sxs-lookup"><span data-stu-id="a2125-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="a2125-118">Se l'esecuzione del comando richiede più tempo rispetto al valore specificato in **millesecondsTimeout**, il comando non riesce con l'eccezione: "Timeout dell'operazione".</span><span class="sxs-lookup"><span data-stu-id="a2125-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="a2125-119">**Script** - System.Management.Automation.ScriptBlock or String Il blocco di script da eseguire.</span><span class="sxs-lookup"><span data-stu-id="a2125-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="a2125-120">**\[useNewScope\]** - Valore booleano facoltativo impostato su **$true**
 Se impostato su **$true**, viene creato un nuovo ambito in cui eseguire il comando.</span><span class="sxs-lookup"><span data-stu-id="a2125-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true**
 If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="a2125-121">Non modifica l'ambiente di runtime della scheda di PowerShell specificato dal comando.</span><span class="sxs-lookup"><span data-stu-id="a2125-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="a2125-122">**\[millisecondsTimeout\]** - Numero intero facoltativo impostato su **500** per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="a2125-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="a2125-123">Se il comando non viene completato entro il tempo specificato, genera **TimeoutException** con il messaggio "Timeout dell'operazione".</span><span class="sxs-lookup"><span data-stu-id="a2125-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type “$x” to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="a2125-124">Proprietà</span><span class="sxs-lookup"><span data-stu-id="a2125-124">Properties</span></span>

###  <span data-ttu-id="a2125-125"><a name="AddOnsMenu"></a> AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="a2125-125"><a name="AddOnsMenu"></a> AddOnsMenu</span></span>
  <span data-ttu-id="a2125-126">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-127">Proprietà di sola lettura che ottiene il menu Componenti aggiuntivi per la scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2125-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

###  <span data-ttu-id="a2125-128"><a name="CanExecute"></a> CanInvoke</span><span class="sxs-lookup"><span data-stu-id="a2125-128"><a name="CanExecute"></a> CanInvoke</span></span>
  <span data-ttu-id="a2125-129">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-130">Proprietà di sola lettura booleana che restituisce un valore **$true** se uno script può essere richiamato con il metodo [Invoke( Script )](#invoke).</span><span class="sxs-lookup"><span data-stu-id="a2125-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

###  <span data-ttu-id="a2125-131"><a name="Commandpane"></a> Consolepane</span><span class="sxs-lookup"><span data-stu-id="a2125-131"><a name="Commandpane"></a> Consolepane</span></span>
  <span data-ttu-id="a2125-132">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a2125-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="a2125-133">In Windows PowerShell ISE 2.0 era denominato **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="a2125-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="a2125-134">Proprietà di sola lettura che ottiene l'oggetto [editor](../ise/The-ISEEditor-Object.md) del riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="a2125-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <span data-ttu-id="a2125-135"><a name="Displayname"></a>DisplayName</span><span class="sxs-lookup"><span data-stu-id="a2125-135"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="a2125-136">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-137">Proprietà di lettura/scrittura che ottiene o imposta il testo visualizzato nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2125-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab.</span></span> <span data-ttu-id="a2125-138">Per impostazione predefinita, le schede sono denominate "PowerShell #", dove # rappresenta un numero.</span><span class="sxs-lookup"><span data-stu-id="a2125-138">By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <span data-ttu-id="a2125-139"><a name="ExpandedScript"></a> ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="a2125-139"><a name="ExpandedScript"></a> ExpandedScript</span></span>
  <span data-ttu-id="a2125-140">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-141">Proprietà di lettura/scrittura booleana che determina se il riquadro di script è espanso o nascosto.</span><span class="sxs-lookup"><span data-stu-id="a2125-141">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <span data-ttu-id="a2125-142"><a name="Files"></a> Files</span><span class="sxs-lookup"><span data-stu-id="a2125-142"><a name="Files"></a> Files</span></span>
  <span data-ttu-id="a2125-143">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-144">Proprietà di sola lettura che ottiene la [raccolta di file di script](../ise/The-ISEFileCollection-Object.md) aperti nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2125-144">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <span data-ttu-id="a2125-145"><a name="Output"></a> Output</span><span class="sxs-lookup"><span data-stu-id="a2125-145"><a name="Output"></a> Output</span></span>
  <span data-ttu-id="a2125-146">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="a2125-146">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="a2125-147">Nelle versioni successive di Windows PowerShell ISE, è possibile usare l'oggetto **ConsolePane** per gli stessi scopi.</span><span class="sxs-lookup"><span data-stu-id="a2125-147">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="a2125-148">Proprietà di sola lettura che ottiene il riquadro di output dell'[editor](../ise/The-ISEEditor-Object.md) corrente.</span><span class="sxs-lookup"><span data-stu-id="a2125-148">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <span data-ttu-id="a2125-149"><a name="Prompt"></a> Prompt</span><span class="sxs-lookup"><span data-stu-id="a2125-149"><a name="Prompt"></a> Prompt</span></span>
  <span data-ttu-id="a2125-150">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-150">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-151">Proprietà di sola lettura che ottiene il testo della richiesta corrente.</span><span class="sxs-lookup"><span data-stu-id="a2125-151">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="a2125-152">Nota: la funzione **Prompt** può essere sostituita dal profilo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a2125-152">Note: the **Prompt** function can be overridden by the user’s profile.</span></span> <span data-ttu-id="a2125-153">Se il risultato è diverso da una stringa semplice, questa proprietà restituisce nothing.</span><span class="sxs-lookup"><span data-stu-id="a2125-153">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <span data-ttu-id="a2125-154"><a name="ShowCommands"></a> ShowCommands</span><span class="sxs-lookup"><span data-stu-id="a2125-154"><a name="ShowCommands"></a> ShowCommands</span></span>
  <span data-ttu-id="a2125-155">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a2125-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="a2125-156">Proprietà di lettura/scrittura che indica se il riquadro dei comandi è attualmente visualizzato.</span><span class="sxs-lookup"><span data-stu-id="a2125-156">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <span data-ttu-id="a2125-157"><a name="StatusText"></a> StatusText</span><span class="sxs-lookup"><span data-stu-id="a2125-157"><a name="StatusText"></a> StatusText</span></span>
  <span data-ttu-id="a2125-158">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a2125-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="a2125-159">Proprietà di sola lettura che ottiene il testo dello stato di **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="a2125-159">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <span data-ttu-id="a2125-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="a2125-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="a2125-161">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a2125-161">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="a2125-162">Proprietà di sola lettura che indica se il riquadro dello strumento Componenti aggiuntivi orizzontale è attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="a2125-162">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <span data-ttu-id="a2125-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span><span class="sxs-lookup"><span data-stu-id="a2125-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span></span>
  <span data-ttu-id="a2125-164">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a2125-164">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="a2125-165">Proprietà di sola lettura che indica se il riquadro dello strumento Componenti aggiuntivi verticale è attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="a2125-165">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="a2125-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a2125-166">See Also</span></span>
- [<span data-ttu-id="a2125-167">Oggetto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="a2125-167">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="a2125-168">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a2125-168">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="a2125-169">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a2125-169">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="a2125-170">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="a2125-170">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
