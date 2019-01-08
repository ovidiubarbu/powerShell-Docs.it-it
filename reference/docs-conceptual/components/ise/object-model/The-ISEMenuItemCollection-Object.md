---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401885"
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

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Clear\(\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Rimuove tutti i sottomenu dalla voce di menu.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISEMenuItem](The-ISEMenuItem-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)