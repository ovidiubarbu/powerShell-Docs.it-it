---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: Oggetto ObjectModelRoot
ms.openlocfilehash: 0b04bdb3127edaac7b504556843efb64ee65ed13
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736029"
---
# <a name="the-objectmodelroot-object"></a>Oggetto ObjectModelRoot

L'oggetto `$psISE`, ovvero l'oggetto radice principale in Windows PowerShell® Integrated Scripting Environment (ISE), è un'istanza della classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot. Questo argomento descrive le proprietà dell'oggetto **ObjectModelRoot**.

## <a name="properties"></a>Proprietà

### <a name="currentfile"></a>CurrentFile

> Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene il file, il quale è associato a tale oggetto host con stato attivo.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene la scheda di PowerShell con stato attivo.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene lo strumento aggiuntivo di Windows PowerShell ISE attualmente visibile che si trova nel riquadro strumenti orizzontale nella parte inferiore dell'editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene lo strumento aggiuntivo di Windows PowerShell ISE attualmente visibile che si trova nel riquadro strumenti verticale nella parte destra dell'editor.

### <a name="options"></a>Opzioni

> Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene le varie opzioni che possono modificare le impostazioni in Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Supportato in Windows PowerShell ISE 2.0 e versioni successive.

Proprietà di sola lettura che ottiene la raccolta di schede di PowerShell, che sono aperte in Windows PowerShell ISE. Per impostazione predefinita, questo oggetto contiene una sola scheda di PowerShell. Tuttavia, è possibile aggiungere altre schede di PowerShell a questo oggetto usando gli script o i menu di Windows PowerShell ISE.

## <a name="see-also"></a>Vedere anche

- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)