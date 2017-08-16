---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Oggetto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a>Oggetto ISEMenuItemCollection
  Un oggetto **ISEMenuItemCollection** è una raccolta di oggetti **ISEMenuItem**. È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**, usato per personalizzare il menu **Componenti aggiuntivi** in Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metodo

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  Supportato in Windows PowerShell ISE 2.0 e versioni successive. 

 Aggiunge una voce di menu alla raccolta.

 **DisplayName** Nome visualizzato del menu da aggiungere.

 **Action** Oggetto **System.Management.Automation.ScriptBlock** che specifica l'azione associata alla voce di menu.

 **Shortcut** Tasto di scelta rapida per l'azione.

 **Returns** Oggetto ISEMenuItem appena aggiunto.

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

  
