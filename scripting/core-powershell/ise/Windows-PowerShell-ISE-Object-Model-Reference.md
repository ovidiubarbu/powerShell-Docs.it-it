---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Riferimenti al modello a oggetti di Windows PowerShell ISE
ms.technology: powershell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 8bcb8620d668abb4d5026e3940fc322cbcfcd523
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="windows-powershell-ise-object-model-reference"></a>Riferimenti al modello a oggetti di Windows PowerShell ISE
  
## <a name="object-model-reference"></a>Riferimento del modello a oggetti
 Questa sezione offre un riferimento per le classi sottostanti che definiscono i vari oggetti in Windows PowerShell® Integrated Scripting Environment (ISE). Per visualizzare gli oggetti organizzati nella relativa gerarchia, vedere [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md).

 [Oggetto ISEAddOnTool](The-ISEAddOnTool-Object.md)
 Esempi: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [Oggetto ISEAddOnTool](The-ISEAddOnTool-Object.md)
  [Oggetto ISEEditor](The-ISEEditor-Object.md)
 Esempi: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [Oggetto ISEFile](The-ISEFile-Object.md)
 Esempi: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [Oggetto ISEFileCollection](The-ISEFileCollection-Object.md)
 Esempi: $psISE.PowerShellTabs.Files.

 [Oggetto ISEMenuItem](The-ISEMenuItem-Object.md)
 Esempi: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [Oggetto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
 Esempio: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [Oggetto ISEOptions](The-ISEOptions-Object.md)
 Esempi: $psISE.Options, $psISE.Options.DefaultOptions.

 [Oggetto ObjectModelRoot](The-ObjectModelRoot-Object.md)
 Esempio: The root $psISE object.

 [Oggetto PowerShellTab](The-PowerShellTab-Object.md)
 Esempi: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [Oggetto PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
 Esempio: $psISE.PowerShellTabs.

## <a name="see-also"></a>Vedere anche
- [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
