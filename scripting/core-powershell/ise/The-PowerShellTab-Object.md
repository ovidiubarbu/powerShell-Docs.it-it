---
title: Oggetto PowerShellTab
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
---
# Oggetto PowerShellTab
  L'oggetto **PowerShellTab** rappresenta un ambiente di runtime di Windows PowerShell.

## Metodo

###  <a name="invoke"></a> Invoke(Script)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Esegue lo script specificato nella scheda di PowerShell.

> [!NOTE]
>  Questo metodo funziona solo su altre schede di PowerShell, non sulla scheda da cui viene eseguito. Non restituisce oggetti o valori. Se il codice modifica una variabile, le modifiche vengono mantenute nella scheda in cui è stato richiamato il comando.

 **Script** - System.Management.Automation.ScriptBlock o String
 Blocco di script da eseguire.

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### InvokeSynchronous(Script, [useNewScope], millisecondsTimeout)
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Esegue lo script specificato nella scheda di PowerShell.

> [!NOTE]
>  Questo metodo funziona solo su altre schede di PowerShell, non sulla scheda da cui viene eseguito. Il blocco di script viene eseguito e qualsiasi valore restituito dallo script viene restituito all'ambiente di esecuzione da cui è stato richiamato il comando. Se l'esecuzione del comando richiede più tempo rispetto al valore specificato in **millesecondsTimeout**, il comando non riesce con l'eccezione: "Timeout dell'operazione".

 **Script** - System.Management.Automation.ScriptBlock o String
 Blocco di script da eseguire.

 **[useNewScope]** - Valore booleano facoltativo che impostato su **$true** per impostazione predefinita.
 Se impostato su **$true**, viene creato un nuovo ambito all'interno del quale eseguire il comando. Non modifica l'ambiente di runtime della scheda di PowerShell specificato dal comando.

 **[millisecondsTimeout]** - Valore intero facoltativo impostato su **500** per impostazione predefinita..
 Se il comando non viene completato entro il tempo specificato, genera **TimeoutException** con il messaggio "Timeout dell'operazione".

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

## Proprietà

###  <a name="AddOnsMenu"></a> AddOnsMenu
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il menu Componenti aggiuntivi per la scheda di PowerShell.

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

###  <a name="CanExecute"></a> CanInvoke
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura booleana che restituisce un valore **$true** se uno script può essere richiamato con il metodo [Invoke( Script )](#invoke).

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

###  <a name="Commandpane"></a> Consolepane
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.  In Windows PowerShell ISE 2.0 era denominato **CommandPane**..

 Proprietà di sola lettura che ottiene l'oggetto [editor](../ise/The-ISEEditor-Object.md) del riquadro della console.

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <a name="Displayname"></a> DisplayName
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di lettura/scrittura che ottiene o imposta il testo visualizzato nella scheda di PowerShell. Per impostazione predefinita, le schede sono denominate "PowerShell#", dove # rappresenta un numero.

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <a name="ExpandedScript"></a> ExpandedScript
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di lettura/scrittura booleana che determina se il riquadro di script è espanso o nascosto.

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <a name="Files"></a> File
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene la [raccolta di file di script](../ise/The-ISEFileCollection-Object.md) aperti nella scheda di PowerShell.

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <a name="Output"></a> Output
  Questa funzionalità è presente in Windows PowerShell ISE 2.0, ma è stata rimossa o rinominata nelle versioni successive di ISE.  Nelle versioni successive di Windows PowerShell ISE, è possibile usare l'oggetto **ConsolePane** per gli stessi scopi.

 Proprietà di sola lettura che ottiene il riquadro di output del'[editor](../ise/The-ISEEditor-Object.md) corrente..

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <a name="Prompt"></a> Prompt
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il testo della richiesta corrente. Nota: la funzione **Prompt** può essere sostituita dal profilo dell'utente. Se il risultato è diverso da una stringa semplice, questa proprietà restituisce nothing.

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <a name="ShowCommands"></a> ShowCommands
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di lettura/scrittura che indica se il riquadro dei comandi è attualmente visualizzato.

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <a name="StatusText"></a> StatusText
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Proprietà di sola lettura che ottiene il testo dello stato di **PowerShellTab**.

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di sola lettura che indica se il riquadro dello strumento Componenti aggiuntivi orizzontale è attualmente aperto.

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**
  Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti. 

 Proprietà di sola lettura che indica se il riquadro dello strumento Componenti aggiuntivi verticale è attualmente aperto.

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## Vedere anche
 [Oggetto PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 
 [Modello a oggetti di scripting di Windows PowerShell ISE](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


