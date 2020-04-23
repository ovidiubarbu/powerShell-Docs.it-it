---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto PowerShellTab
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402518"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="8057c-103">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="8057c-103">The PowerShellTab Object</span></span>

<span data-ttu-id="8057c-104">L'oggetto **PowerShellTab** rappresenta un ambiente di runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8057c-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="8057c-105">Metodi</span><span class="sxs-lookup"><span data-stu-id="8057c-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="8057c-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="8057c-106">Invoke\( Script \)</span></span>

<span data-ttu-id="8057c-107">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-108">Esegue lo script specificato nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8057c-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="8057c-109">Questo metodo funziona solo su altre schede di PowerShell, non sulla scheda da cui viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="8057c-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="8057c-110">Non restituisce oggetti o valori.</span><span class="sxs-lookup"><span data-stu-id="8057c-110">It does not return any object or value.</span></span> <span data-ttu-id="8057c-111">Se il codice modifica una variabile, le modifiche vengono mantenute nella scheda in cui è stato richiamato il comando.</span><span class="sxs-lookup"><span data-stu-id="8057c-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="8057c-112">**Script** - System.Management.Automation.ScriptBlock or String Il blocco di script da eseguire.</span><span class="sxs-lookup"><span data-stu-id="8057c-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="8057c-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="8057c-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="8057c-114">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="8057c-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8057c-115">Esegue lo script specificato nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8057c-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="8057c-116">Questo metodo funziona solo su altre schede di PowerShell, non sulla scheda da cui viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="8057c-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="8057c-117">Il blocco di script viene eseguito e qualsiasi valore restituito dallo script viene restituito all'ambiente di esecuzione da cui è stato richiamato il comando.</span><span class="sxs-lookup"><span data-stu-id="8057c-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="8057c-118">Se l'esecuzione del comando richiede più tempo rispetto al valore specificato in **millesecondsTimeout**, il comando non riesce con l'eccezione: "Timeout dell'operazione."</span><span class="sxs-lookup"><span data-stu-id="8057c-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="8057c-119">**Script** - System.Management.Automation.ScriptBlock or String Il blocco di script da eseguire.</span><span class="sxs-lookup"><span data-stu-id="8057c-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="8057c-120">**\[useNewScope\]** - Valore booleano facoltativo impostato su `$true`per impostazione predefinita. Se impostato su `$true`, viene creato un nuovo ambito in cui eseguire il comando.</span><span class="sxs-lookup"><span data-stu-id="8057c-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="8057c-121">Non modifica l'ambiente di runtime della scheda di PowerShell specificato dal comando.</span><span class="sxs-lookup"><span data-stu-id="8057c-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="8057c-122">**\[millisecondsTimeout\]** - Numero intero facoltativo impostato su **500** per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="8057c-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="8057c-123">Se il comando non viene completato entro il tempo specificato, genera **TimeoutException** con il messaggio "Timeout dell'operazione".</span><span class="sxs-lookup"><span data-stu-id="8057c-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="8057c-124">Proprietà</span><span class="sxs-lookup"><span data-stu-id="8057c-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="8057c-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="8057c-125">AddOnsMenu</span></span>

<span data-ttu-id="8057c-126">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-127">Proprietà di sola lettura che ottiene il menu Componenti aggiuntivi per la scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8057c-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="8057c-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="8057c-128">CanInvoke</span></span>

<span data-ttu-id="8057c-129">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-130">Proprietà di sola lettura booleana che restituisce un valore `$true` se uno script può essere chiamato con il metodo [Invoke( Script )](#invoke-script-).</span><span class="sxs-lookup"><span data-stu-id="8057c-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="8057c-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="8057c-131">ConsolePane</span></span>

<span data-ttu-id="8057c-132">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="8057c-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="8057c-133">In Windows PowerShell ISE 2.0 era denominato **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="8057c-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="8057c-134">Proprietà di sola lettura che ottiene l'oggetto [editor](The-ISEEditor-Object.md) del riquadro della console.</span><span class="sxs-lookup"><span data-stu-id="8057c-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="8057c-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8057c-135">DisplayName</span></span>

<span data-ttu-id="8057c-136">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-137">Proprietà di lettura/scrittura che ottiene o imposta il testo visualizzato nella scheda di PowerShell. Per impostazione predefinita, le schede sono denominate "PowerShell #", dove # rappresenta un numero.</span><span class="sxs-lookup"><span data-stu-id="8057c-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="8057c-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="8057c-138">ExpandedScript</span></span>

<span data-ttu-id="8057c-139">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-140">Proprietà di lettura/scrittura booleana che determina se il riquadro di script è espanso o nascosto.</span><span class="sxs-lookup"><span data-stu-id="8057c-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="8057c-141">File</span><span class="sxs-lookup"><span data-stu-id="8057c-141">Files</span></span>

<span data-ttu-id="8057c-142">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-143">Proprietà di sola lettura che ottiene la [raccolta di file di script](The-ISEFileCollection-Object.md) aperti nella scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8057c-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="8057c-144">Output</span><span class="sxs-lookup"><span data-stu-id="8057c-144">Output</span></span>

<span data-ttu-id="8057c-145">Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.</span><span class="sxs-lookup"><span data-stu-id="8057c-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="8057c-146">Nelle versioni successive di Windows PowerShell ISE, è possibile usare l'oggetto **ConsolePane** per gli stessi scopi.</span><span class="sxs-lookup"><span data-stu-id="8057c-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="8057c-147">Proprietà di sola lettura che ottiene il riquadro di output dell'[editor](The-ISEEditor-Object.md) corrente.</span><span class="sxs-lookup"><span data-stu-id="8057c-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="8057c-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="8057c-148">Prompt</span></span>

<span data-ttu-id="8057c-149">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-150">Proprietà di sola lettura che ottiene il testo della richiesta corrente.</span><span class="sxs-lookup"><span data-stu-id="8057c-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="8057c-151">Nota: la funzione **Prompt** può essere sostituita dal profilo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8057c-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="8057c-152">Se il risultato è diverso da una stringa semplice, questa proprietà restituisce nothing.</span><span class="sxs-lookup"><span data-stu-id="8057c-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="8057c-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="8057c-153">ShowCommands</span></span>

<span data-ttu-id="8057c-154">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="8057c-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8057c-155">Proprietà di lettura/scrittura che indica se il riquadro dei comandi è attualmente visualizzato.</span><span class="sxs-lookup"><span data-stu-id="8057c-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="8057c-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="8057c-156">StatusText</span></span>

<span data-ttu-id="8057c-157">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8057c-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8057c-158">Proprietà di sola lettura che ottiene il testo dello stato di **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="8057c-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="8057c-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="8057c-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="8057c-160">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="8057c-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8057c-161">Proprietà di sola lettura che indica se il riquadro dello strumento Componenti aggiuntivi orizzontale è attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="8057c-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="8057c-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="8057c-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="8057c-163">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="8057c-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8057c-164">Proprietà di sola lettura che indica se il riquadro dello strumento Componenti aggiuntivi verticale è attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="8057c-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="8057c-165">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8057c-165">See Also</span></span>

- [<span data-ttu-id="8057c-166">Oggetto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="8057c-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="8057c-167">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8057c-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="8057c-168">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="8057c-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
