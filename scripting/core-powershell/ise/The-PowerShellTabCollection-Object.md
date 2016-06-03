---
title:  Oggetto PowerShellTabCollection
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  81f4bf4a-83bf-415e-8378-1703792fbb58
---

# Oggetto PowerShellTabCollection
  L'oggetto della raccolta **PowerShellTab** è una raccolta di oggetti **PowerShellTab**. Ogni oggetto **PowerShellTab** funziona come un ambiente di runtime separato. È un'istanza della classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. Un esempio è l'oggetto **$psISE.PowerShellTabs**.

## Metodo

### Add()
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Aggiunge una nuova scheda di PowerShell alla raccolta. Restituisce la scheda appena aggiunta.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### Remove(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Rimuove la scheda specificata dal parametro **psTab**.

 **psTab**
 Scheda di PowerShell da rimuovere.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### SetSelectedPowerShellTab(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Seleziona la scheda di PowerShell specificata dal parametro **psTab** in modo che diventi la scheda di PowerShell attualmente attiva.

 **psTab**
 Scheda di PowerShell da selezionare.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## Vedere anche
 [Oggetto PowerShellTab](The-PowerShellTab-Object.md) 
 [The Windows PowerShell ISE Scripting Object Model](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) (Modello a oggetti di scripting di Windows PowerShell ISE) 
 [Riferimenti al modello a oggetti di Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Gerarchia del modello a oggetti ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


