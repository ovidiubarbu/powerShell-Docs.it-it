---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Oggetto ISEMenuItemCollection
ms.technology: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 45e9123df5f22f37d2a76e49db6df5aa98824e1c
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isemenuitemcollection-object"></a>Oggetto ISEMenuItemCollection
  Un oggetto **ISEMenuItemCollection** è una raccolta di oggetti **ISEMenuItem**. È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**, usato per personalizzare il menu **Componenti aggiuntivi** in Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metodo

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Aggiunge una voce di menu alla raccolta.

 **DisplayName**
Il nome visualizzato del menu da aggiungere.

 **Action**
 Oggetto **System.Management.Automation.ScriptBlock** che specifica l'azione associata alla voce di menu.

 **Shortcut**
 Tasto di scelta rapida per l'azione.

 **Returns**
 Oggetto ISEMenuItem appena aggiunto.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Clear\(\)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Rimuove tutti i sottomenu dalla voce di menu.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Vedere anche
- [Oggetto ISEMenuItem](The-ISEMenuItem-Object.md) 
- [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)

  
