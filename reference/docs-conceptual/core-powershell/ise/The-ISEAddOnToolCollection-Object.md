---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontoolcollection-object"></a>Oggetto ISEAddOnToolCollection

L'oggetto **ISEAddOnToolCollection** è una raccolta di oggetti **ISEAddOnTool**. Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.

## <a name="methods"></a>Metodi

### <a name="add-name-controltype-isvisible-"></a>Add\( Name, ControlType, \[IsVisible\] \)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Aggiunge un nuovo strumento aggiuntivo alla raccolta. Restituisce lo strumento aggiuntivo appena aggiunto. Prima di eseguire questo comando, è necessario installare lo strumento aggiuntivo nel computer locale e caricare l'assembly.

**Name**: la stringa specifica il nome visualizzato dello strumento aggiuntivo aggiunto a Windows PowerShell ISE.

**ControlType**: il tipo specifica il controllo aggiunto.

**\[IsVisible\]**: valore booleano facoltativo che se impostato su **$true** rende visibile lo strumento aggiuntivo nel riquadro associato degli strumenti.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Rimuove lo strumento aggiuntivo specificato dalla raccolta.

**Item**: Microsoft.PowerShell.Host.ISE.ISEAddOnTool specifica l'oggetto che deve essere rimosso da Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Seleziona la scheda di PowerShell specificata dal parametro **psTab**.

**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da selezionare.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Rimuove la scheda di PowerShell specificata dal parametro **psTab**.

**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da rimuovere.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Vedere anche

- [Oggetto PowerShellTab](The-PowerShellTab-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)