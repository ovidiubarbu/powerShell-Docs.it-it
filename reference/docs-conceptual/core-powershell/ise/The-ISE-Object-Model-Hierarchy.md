---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Gerarchia del modello a oggetti ISE
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a>Gerarchia del modello a oggetti ISE
  Questo argomento illustra la gerarchia di oggetti che fanno parte di Windows PowerShell Integrated Scripting Environment (ISE). Windows PowerShell ISE è incluso in Windows PowerShell 3.0 e in Windows PowerShell 4.0. Fare clic su un oggetto per accedere alla documentazione di riferimento per la classe che definisce l'oggetto.

##  <a name="psise-object"></a>**Oggetto $psISE**
 L'oggetto **$psISE** è l'[oggetto radice](The-ObjectModelRoot-Object.md) della gerarchia di oggetti di Windows PowerShell ISE. Si trova al livello superiore, rendendo disponibili gli oggetti seguenti per lo scripting:

-   **[$psISE.CurrentFile]()**

-   **[$psISE.CurrentPowerShellTab]()**

-   **[$psISE.CurrentVisibleHorizontalTool]()**

-   **[$psISE.CurrentVisibleVerticalTool]()**

-   **[$psISE.Options]()**

-   **[$psISE.PowerShellTabs]()**

##  <a name="psisecurrentfilethe-isefile-objectmd"></a>**[$psISE.CurrentFile](The-ISEFile-Object.md)**
 L'oggetto **$psISE.CurrentFile** è un'istanza della classe [ISEFile](The-ISEFile-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:

-   **[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**

-   **[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**: questo oggetto è un'istanza della classe [ISEEditor](The-ISEEditor-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:

    -   **[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**

    -   **[CaretColumn](The-ISEEditor-Object.md)**

    -   **[CaretLine](The-ISEEditor-Object.md)**

    -   **[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**

    -   **[LineCount](The-ISEEditor-Object.md)**

    -   **[SelectedText](The-ISEEditor-Object.md)**

    -   **[Text](The-ISEEditor-Object.md)**

-   **[EncodingThe-ISEFile-Object.md]()**

-   **[FullPathThe-ISEFile-Object.md]()**

-   **[IsSavedThe-ISEFile-Object.md]()**

-   **[IsUntitledThe-ISEFile-Object.md]()**

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**
 L'oggetto **$psISE.CurrentPowerShellTab** è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:

-   **[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**: questo oggetto è un'istanza della classe [ISEMenuItem](The-ISEMenuItem-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**: questo oggetto è un'istanza della classe [ISEEditor](The-ISEEditor-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**

    -   **[CaretColumnThe-ISEEditor-Object.md]()**

    -   **[CaretLineThe-ISEEditor-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**

    -   **[LineCountThe-ISEEditor-Object.md]()**

    -   **[SelectedTextThe-ISEEditor-Object.md]()**

    -   **[TextThe-ISEEditor-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

##  <a name="psisecurrentvisiblehorizontaltool"></a>**$psISE.CurrentVisibleHorizontalTool**
 L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo superiore della finestra di Windows PowerShell ISE. Questo oggetto rende disponibili gli oggetti seguenti per lo scripting:

-   **[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**

##  <a name="psisecurrentvisibleverticaltool"></a>**$psISE.CurrentVisibleVerticalTool**
 L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo destro della finestra di Windows PowerShell ISE. Questo oggetto rende disponibili gli oggetti seguenti per lo scripting:

-   **[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**

##  <a name="psiseoptions"></a>**$psISE.Options**
 L'oggetto **$psISE.Options** rende disponibili gli oggetti seguenti per lo scripting:

-   **[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**

-   **[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**

-   **[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**
 L'oggetto **$psISE.PowerShellTabs** è un'istanza della classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). È una raccolta di tutte le schede di PowerShell attualmente aperte che rappresentano gli ambienti di esecuzione di Windows PowerShell disponibili nel computer locale o nei computer remoti connessi. Ogni membro della raccolta è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Vedere anche
- [Modello a oggetti di scripting di Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Riferimenti al modello a oggetti di Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)

