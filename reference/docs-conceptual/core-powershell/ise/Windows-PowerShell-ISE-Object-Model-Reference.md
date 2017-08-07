---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Riferimenti al modello a oggetti di Windows PowerShell ISE
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: e5d4ae03158d9b5b0efd98db1272bc13872181ac
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="d4fe9-103">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d4fe9-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="d4fe9-104">Riferimento del modello a oggetti</span><span class="sxs-lookup"><span data-stu-id="d4fe9-104">Object Model Reference</span></span>
 <span data-ttu-id="d4fe9-105">Questa sezione offre un riferimento per le classi sottostanti che definiscono i vari oggetti in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d4fe9-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="d4fe9-106">Per visualizzare gli oggetti organizzati nella relativa gerarchia, vedere [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="d4fe9-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="d4fe9-107">[Oggetto ISEAddOnTool](The-ISEAddOnTool-Object.md)
 Esempi: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md)
 Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="d4fe9-108">[Oggetto ISEAddOnTool](The-ISEAddOnTool-Object.md)
  [Oggetto ISEEditor](The-ISEEditor-Object.md)
 Esempi: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md)
  [The ISEEditor Object](The-ISEEditor-Object.md)
 Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="d4fe9-109">[Oggetto ISEFile](The-ISEFile-Object.md)
 Esempi: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="d4fe9-109">[The ISEFile Object](The-ISEFile-Object.md)
 Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="d4fe9-110">[Oggetto ISEFileCollection](The-ISEFileCollection-Object.md)
 Esempi: $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md)
 Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="d4fe9-111">[Oggetto ISEMenuItem](The-ISEMenuItem-Object.md)
 Esempi: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="d4fe9-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md)
 Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="d4fe9-112">[Oggetto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
 Esempio: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md)
 Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="d4fe9-113">[Oggetto ISEOptions](The-ISEOptions-Object.md)
 Esempi: $psISE.Options, $psISE.Options.DefaultOptions.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-113">[The ISEOptions Object](The-ISEOptions-Object.md)
 Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="d4fe9-114">[Oggetto ObjectModelRoot](The-ObjectModelRoot-Object.md)
 Esempio: The root $psISE object.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md)
 Example: The root $psISE object.</span></span>

 <span data-ttu-id="d4fe9-115">[Oggetto PowerShellTab](The-PowerShellTab-Object.md)
 Esempi: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="d4fe9-115">[The PowerShellTab Object](The-PowerShellTab-Object.md)
 Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="d4fe9-116">[Oggetto PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
 Esempio: $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="d4fe9-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md)
 Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4fe9-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d4fe9-117">See Also</span></span>
- [<span data-ttu-id="d4fe9-118">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d4fe9-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
