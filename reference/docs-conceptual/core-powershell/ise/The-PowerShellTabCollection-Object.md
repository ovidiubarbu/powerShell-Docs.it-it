---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershelltabcollection-object"></a>Oggetto PowerShellTabCollection

L'oggetto della raccolta **PowerShellTab** è una raccolta di oggetti **PowerShellTab**. Ogni oggetto **PowerShellTab** funziona come un ambiente di runtime separato. È un'istanza della classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. Un esempio è l'oggetto **$psISE.PowerShellTabs**.

## <a name="methods"></a>Metodi

### <a name="add"></a>Add\(\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Aggiunge una nuova scheda di PowerShell alla raccolta. Restituisce la scheda appena aggiunta.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Rimuove la scheda specificata dal parametro **psTab**.

**psTab** Scheda di PowerShell da rimuovere.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Seleziona la scheda di PowerShell specificata dal parametro **psTab** in modo che diventi la scheda di PowerShell attualmente attiva.

**psTab** Scheda di PowerShell da selezionare.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Vedere anche

- [Oggetto PowerShellTab](The-PowerShellTab-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)