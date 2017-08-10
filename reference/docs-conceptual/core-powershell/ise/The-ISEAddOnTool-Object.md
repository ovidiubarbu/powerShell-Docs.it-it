---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: 15f0cdd1425b9f87edeb0404fc385275e4a9d1d8
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="f06bb-103">Oggetto ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="f06bb-103">The ISEAddOnTool Object</span></span>
  <span data-ttu-id="f06bb-104">Un oggetto **ISEAddonTool** rappresenta uno strumento aggiuntivo installato che offre funzionalità aggiuntive per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f06bb-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="f06bb-105">Un esempio è lo strumento **Comandi** che è possibile visualizzare facendo clic su **Visualizza** quindi su **Mostra componente aggiuntivo comandi**.</span><span class="sxs-lookup"><span data-stu-id="f06bb-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="f06bb-106">Questo strumento è quindi accessibile all'utente modificando i vari oggetti **ISEAddOnTool** disponibili.</span><span class="sxs-lookup"><span data-stu-id="f06bb-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

 <span data-ttu-id="f06bb-107">Ogni strumento aggiuntivo può essere associato al riquadro verticale oppure orizzontale.</span><span class="sxs-lookup"><span data-stu-id="f06bb-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="f06bb-108">Il riquadro verticale è ancorato al bordo destro di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f06bb-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="f06bb-109">Il riquadro orizzontale è ancorato al bordo inferiore.</span><span class="sxs-lookup"><span data-stu-id="f06bb-109">The horizontal pane is docked to the bottom edge.</span></span>

 <span data-ttu-id="f06bb-110">Ogni scheda di PowerShell in Windows PowerShell ISE può avere un proprio set di strumenti aggiuntivi installati.</span><span class="sxs-lookup"><span data-stu-id="f06bb-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="f06bb-111">Vedere [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) per accedere alla raccolta di strumenti disponibili nella scheda attualmente selezionate oppure le stesse proprietà in uno qualsiasi degli oggetti **PowerShellTab** nella raccolta di oggetti [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f06bb-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="f06bb-112">Metodo</span><span class="sxs-lookup"><span data-stu-id="f06bb-112">Methods</span></span>
 <span data-ttu-id="f06bb-113">Non sono disponibili metodi specifici di Windows PowerShell ISE per gli oggetti di questa classe.</span><span class="sxs-lookup"><span data-stu-id="f06bb-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="f06bb-114">Proprietà</span><span class="sxs-lookup"><span data-stu-id="f06bb-114">Properties</span></span>

###  <span data-ttu-id="f06bb-115"><a name="Control"></a> Control</span><span class="sxs-lookup"><span data-stu-id="f06bb-115"><a name="Control"></a> Control</span></span>
  <span data-ttu-id="f06bb-116">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f06bb-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="f06bb-117">La proprietà **Control** offre l'accesso in lettura a molte informazioni dettagliate sullo strumento aggiuntivo Comandi.</span><span class="sxs-lookup"><span data-stu-id="f06bb-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
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

###  <span data-ttu-id="f06bb-118"><a name="IsVisible"></a> IsVisible</span><span class="sxs-lookup"><span data-stu-id="f06bb-118"><a name="IsVisible"></a> IsVisible</span></span>
  <span data-ttu-id="f06bb-119">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f06bb-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="f06bb-120">Proprietà booleana che indica se lo strumento aggiuntivo è attualmente visibile nel relativo riquadro assegnato.</span><span class="sxs-lookup"><span data-stu-id="f06bb-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="f06bb-121">Se è visibile, è possibile impostare la proprietà **IsVisible** su **$false** per nascondere lo strumento oppure impostare la proprietà **IsVisible** su **$true** per rendere uno strumento aggiuntivo visibile nella relativa scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f06bb-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab.</span></span> <span data-ttu-id="f06bb-122">Quando uno strumento aggiuntivo è nascosto, non è più accessibile attraverso gli oggetti **CurrentVisibleHorizontalTool** o **CurrentVisibleVerticalTool** e quindi non può essere reso visibile usando questa proprietà su tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="f06bb-122">Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

###  <span data-ttu-id="f06bb-123"><a name="name"></a> Name</span><span class="sxs-lookup"><span data-stu-id="f06bb-123"><a name="name"></a> Name</span></span>
  <span data-ttu-id="f06bb-124">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="f06bb-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="f06bb-125">Proprietà di sola lettura che ottiene il nome dello strumento aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="f06bb-125">The read-only property that gets the name of the add-on tool.</span></span>

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a><span data-ttu-id="f06bb-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f06bb-126">See Also</span></span>
- [<span data-ttu-id="f06bb-127">Oggetto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="f06bb-127">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="f06bb-128">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f06bb-128">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f06bb-129">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f06bb-129">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="f06bb-130">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="f06bb-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
