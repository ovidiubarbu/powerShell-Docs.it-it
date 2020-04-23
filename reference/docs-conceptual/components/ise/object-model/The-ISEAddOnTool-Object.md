---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEAddOnTool
ms.openlocfilehash: a5357005ec1a883f5a14882a42e3150e09ff33a2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736131"
---
# <a name="the-iseaddontool-object"></a>Oggetto ISEAddOnTool

Un oggetto **ISEAddonTool** rappresenta uno strumento aggiuntivo installato che offre funzionalità aggiuntive per Windows PowerShell ISE. Un esempio è lo strumento **Comandi** che è possibile visualizzare facendo clic su **Visualizza** quindi su **Mostra componente aggiuntivo comandi**. Questo strumento è quindi accessibile all'utente modificando i vari oggetti **ISEAddOnTool** disponibili.

Ogni strumento aggiuntivo può essere associato al riquadro verticale oppure orizzontale. Il riquadro verticale è ancorato al bordo destro di Windows PowerShell ISE. Il riquadro orizzontale è ancorato al bordo inferiore.

Ogni scheda di PowerShell in Windows PowerShell ISE può avere un proprio set di strumenti aggiuntivi installati. Vedere [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) per accedere alla raccolta di strumenti disponibili nella scheda attualmente selezionate oppure le stesse proprietà in uno qualsiasi degli oggetti **PowerShellTab** nella raccolta di oggetti [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).

## <a name="methods"></a>Metodi

Non sono disponibili metodi specifici di Windows PowerShell ISE per gli oggetti di questa classe.

## <a name="properties"></a>Proprietà

### <a name="control"></a>Controllo

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

La proprietà **Control** offre l'accesso in lettura a molte informazioni dettagliate sullo strumento aggiuntivo Comandi.

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
```

```Output
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a>IsVisible

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Proprietà booleana che indica se lo strumento aggiuntivo è attualmente visibile nel relativo riquadro assegnato. Se è visibile, è possibile impostare la proprietà **IsVisible** su `$false` per nascondere lo strumento oppure impostare la proprietà **IsVisible** su `$true` per rendere uno strumento aggiuntivo visibile nella relativa scheda di PowerShell. Quando uno strumento aggiuntivo è nascosto, non è più accessibile attraverso gli oggetti **CurrentVisibleHorizontalTool** o **CurrentVisibleVerticalTool** e quindi non può essere reso visibile usando questa proprietà su tale oggetto.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Nome

Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.

Proprietà di sola lettura che ottiene il nome dello strumento aggiuntivo.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
```

```Output
Commands
```

## <a name="see-also"></a>Vedere anche

- [Oggetto ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Scopo del modello a oggetti di scripting di Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)
