---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISEMenuItem
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736982"
---
# <a name="the-isemenuitem-object"></a>Oggetto ISEMenuItem

Un oggetto **ISEMenuItem** è un'istanza della classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.
Tutti gli oggetti nel menu **Componenti aggiuntivi** sono istanze della classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.

## <a name="properties"></a>Proprietà

### <a name="displayname"></a>DisplayName

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il nome visualizzato della voce di menu.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Azione

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il blocco di script. Richiama l'azione quando si sceglie la voce di menu.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Tasto di scelta rapida

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il tasto di scelta rapida di input per la voce di menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Sottomenu

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene l'[elenco di sottomenu](The-ISEMenuItemCollection-Object.md) della voce di menu.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Esempio di script

Per comprendere meglio l'utilizzo del menu Componenti aggiuntivi e le relative proprietà gestibili tramite script, vedere l'esempio di script seguente.

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
