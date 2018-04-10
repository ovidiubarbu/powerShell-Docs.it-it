---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gerarchia del modello a oggetti ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="f1e4e-103">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="f1e4e-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="f1e4e-104">Questo argomento illustra la gerarchia di oggetti che fanno parte di Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="f1e4e-105">Windows PowerShell ISE è incluso in Windows PowerShell 3.0 e in Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="f1e4e-106">Fare clic su un oggetto per accedere alla documentazione di riferimento per la classe che definisce l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="f1e4e-107">Oggetto $psISE</span><span class="sxs-lookup"><span data-stu-id="f1e4e-107">$psISE Object</span></span>

<span data-ttu-id="f1e4e-108">L'oggetto **$psISE** è l'[oggetto radice](The-ObjectModelRoot-Object.md) della gerarchia di oggetti di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="f1e4e-109">Si trova al livello superiore, rendendo disponibili gli oggetti seguenti per lo scripting:</span><span class="sxs-lookup"><span data-stu-id="f1e4e-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="f1e4e-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="f1e4e-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="f1e4e-111">L'oggetto **$psISE.CurrentFile** è un'istanza della classe [ISEFile](The-ISEFile-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="f1e4e-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="f1e4e-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="f1e4e-113">L'oggetto **$psISE.CurrentPowerShellTab** è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="f1e4e-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="f1e4e-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="f1e4e-115">L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="f1e4e-116">Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo superiore della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="f1e4e-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="f1e4e-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="f1e4e-118">L'oggetto **$psISE.CurrentVisibleHorizontalTool** è un'istanza della classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="f1e4e-119">Rappresenta lo strumento aggiuntivo installato che è attualmente ancorato al bordo destro della finestra di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="f1e4e-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="f1e4e-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="f1e4e-121">L'oggetto **$psISE.Options** è un'istanza della classe [ISEOptions](The-ISEOptions-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="f1e4e-122">L'oggetto ISEOptions rappresenta varie impostazioni per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="f1e4e-123">È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="f1e4e-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="f1e4e-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="f1e4e-125">L'oggetto **$psISE.PowerShellTabs** è un'istanza della classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="f1e4e-126">È una raccolta di tutte le schede di PowerShell attualmente aperte che rappresentano gli ambienti di esecuzione di Windows PowerShell disponibili nel computer locale o nei computer remoti connessi.</span><span class="sxs-lookup"><span data-stu-id="f1e4e-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="f1e4e-127">Ogni membro della raccolta è un'istanza della classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="f1e4e-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1e4e-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1e4e-128">See Also</span></span>

- [<span data-ttu-id="f1e4e-129">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f1e4e-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f1e4e-130">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="f1e4e-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)