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
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="1f3d1-103">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="1f3d1-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="1f3d1-104">Questo argomento illustra la gerarchia di oggetti che fanno parte di Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="1f3d1-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="1f3d1-105">Windows PowerShell ISE è incluso in Windows PowerShell 3.0 e in Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="1f3d1-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="1f3d1-106">Fare clic su un oggetto per accedere alla documentazione di riferimento per la classe che definisce l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="1f3d1-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <a name="psise-object"></a><span data-ttu-id="1f3d1-107">**Oggetto $psISE**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-107">**$psISE Object**</span></span>
 <span data-ttu-id="1f3d1-108">L'oggetto **$psISE** è l'[oggetto radice](The-ObjectModelRoot-Object.md) della gerarchia di oggetti di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f3d1-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="1f3d1-109">Si trova al livello superiore, rendendo disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="1f3d1-110">**[$psISE.CurrentFile]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-110">**[$psISE.CurrentFile]()**</span></span>

-   <span data-ttu-id="1f3d1-111">**[$psISE.CurrentPowerShellTab]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-111">**[$psISE.CurrentPowerShellTab]()**</span></span>

-   <span data-ttu-id="1f3d1-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span></span>

-   <span data-ttu-id="1f3d1-113">**[$psISE.CurrentVisibleVerticalTool]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-113">**[$psISE.CurrentVisibleVerticalTool]()**</span></span>

-   <span data-ttu-id="1f3d1-114">**[$psISE.Options]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-114">**[$psISE.Options]()**</span></span>

-   <span data-ttu-id="1f3d1-115">**[$psISE.PowerShellTabs]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-115">**[$psISE.PowerShellTabs]()**</span></span>

##  <a name="psisecurrentfilethe-isefile-objectmd"></a><span data-ttu-id="1f3d1-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="1f3d1-117">L'oggetto **$psISE.CurrentFile** è un'istanza della classe [ISEFile](The-ISEFile-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="1f3d1-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**: questo oggetto è un'istanza della classe [ISEEditor](The-ISEEditor-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="1f3d1-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="1f3d1-121">**[CaretColumn](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-121">**[CaretColumn](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="1f3d1-122">**[CaretLine](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-122">**[CaretLine](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="1f3d1-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="1f3d1-124">**[LineCount](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-124">**[LineCount](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="1f3d1-125">**[SelectedText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-125">**[SelectedText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="1f3d1-126">**[Text](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-126">**[Text](The-ISEEditor-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-127">**[EncodingThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-127">**[EncodingThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-128">**[FullPathThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-128">**[FullPathThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-129">**[IsSavedThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-129">**[IsSavedThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-130">**[IsUntitledThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-130">**[IsUntitledThe-ISEFile-Object.md]()**</span></span>

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a><span data-ttu-id="1f3d1-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="1f3d1-132">L'oggetto **$psISE.CurrentPowerShellTab** è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="1f3d1-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**: questo oggetto è un'istanza della classe [ISEMenuItem](The-ISEMenuItem-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="1f3d1-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**: questo oggetto è un'istanza della classe [ISEEditor](The-ISEEditor-Object.md) e rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="1f3d1-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-142">**[CaretLineThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-142">**[CaretLineThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-144">**[LineCountThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-144">**[LineCountThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="1f3d1-146">**[TextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-146">**[TextThe-ISEEditor-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="1f3d1-160">**$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-160">**$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="1f3d1-161">L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f3d1-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="1f3d1-162">Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo superiore della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f3d1-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="1f3d1-163">Questo oggetto rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="1f3d1-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="1f3d1-167">**$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-167">**$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="1f3d1-168">L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f3d1-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="1f3d1-169">Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo destro della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1f3d1-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="1f3d1-170">Questo oggetto rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="1f3d1-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psiseoptions"></a><span data-ttu-id="1f3d1-174">**$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-174">**$psISE.Options**</span></span>
 <span data-ttu-id="1f3d1-175">L'oggetto **$psISE.Options** rende disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="1f3d1-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="1f3d1-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="1f3d1-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="1f3d1-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span></span>

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a><span data-ttu-id="1f3d1-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="1f3d1-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="1f3d1-212">L'oggetto **$psISE.PowerShellTabs** è un'istanza della classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f3d1-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="1f3d1-213">È una raccolta di tutte le schede di PowerShell attualmente aperte che rappresentano gli ambienti di esecuzione di Windows PowerShell disponibili nel computer locale o nei computer remoti connessi.</span><span class="sxs-lookup"><span data-stu-id="1f3d1-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="1f3d1-214">Ogni membro della raccolta è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="1f3d1-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f3d1-215">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f3d1-215">See Also</span></span>
- [<span data-ttu-id="1f3d1-216">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1f3d1-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1f3d1-217">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1f3d1-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

