---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Gerarchia del modello a oggetti ISE
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737033"
---
# <a name="the-ise-object-model-hierarchy"></a>Gerarchia del modello a oggetti ISE

Questo argomento illustra la gerarchia di oggetti che fanno parte di Windows PowerShell Integrated Scripting Environment (ISE). Windows PowerShell ISE è incluso in Windows PowerShell 3.0, 4.0 e 5.1. Fare clic su un oggetto per accedere alla documentazione di riferimento per la classe che definisce l'oggetto.

## <a name="psise-object"></a>Oggetto $psISE

L'oggetto `$psISE` è l'[oggetto radice](The-ObjectModelRoot-Object.md) della gerarchia di oggetti di Windows PowerShell ISE. Si trova al livello superiore, rendendo disponibili gli oggetti seguenti per lo scripting:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

L'oggetto `$psISE.CurrentFile` è un'istanza della classe [ISEFile](The-ISEFile-Object.md).

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

L'oggetto `$psISE.CurrentPowerShellTab` è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

L'oggetto `$psISE.CurrentVisibleHorizontalTool` è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo superiore della finestra di Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

L'oggetto `$psISE.CurrentVisibleHorizontalTool` è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo destro della finestra di Windows PowerShell ISE.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

L'oggetto `$psISE.Options` è un'istanza della classe [ISEOptions](The-ISEOptions-Object.md). L'oggetto ISEOptions rappresenta varie impostazioni per Windows PowerShell ISE. È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

L'oggetto `$psISE.PowerShellTabs` è un'istanza della classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). È una raccolta di tutte le schede di PowerShell attualmente aperte che rappresentano gli ambienti di esecuzione di Windows PowerShell disponibili nel computer locale o nei computer remoti connessi. Ogni membro della raccolta è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Vedere anche

- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
