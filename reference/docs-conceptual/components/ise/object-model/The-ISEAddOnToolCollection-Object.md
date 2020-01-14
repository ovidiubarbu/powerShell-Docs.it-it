---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISEAddOnToolCollection
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737016"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="82baa-103">Oggetto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="82baa-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="82baa-104">L'oggetto **ISEAddOnToolCollection** è una raccolta di oggetti **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="82baa-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="82baa-105">Un esempio è l'oggetto `$psISE.CurrentPowerShellTab.VerticalAddOnTools`.</span><span class="sxs-lookup"><span data-stu-id="82baa-105">An example is the `$psISE.CurrentPowerShellTab.VerticalAddOnTools` object.</span></span>

## <a name="methods"></a><span data-ttu-id="82baa-106">Metodi</span><span class="sxs-lookup"><span data-stu-id="82baa-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="82baa-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="82baa-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="82baa-108">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="82baa-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="82baa-109">Aggiunge un nuovo strumento aggiuntivo alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="82baa-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="82baa-110">Restituisce lo strumento aggiuntivo appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="82baa-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="82baa-111">Prima di eseguire questo comando, è necessario installare lo strumento aggiuntivo nel computer locale e caricare l'assembly.</span><span class="sxs-lookup"><span data-stu-id="82baa-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="82baa-112">**Name**: la stringa specifica il nome visualizzato dello strumento aggiuntivo aggiunto a Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="82baa-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="82baa-113">**ControlType**: il tipo specifica il controllo aggiunto.</span><span class="sxs-lookup"><span data-stu-id="82baa-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="82baa-114">**\[IsVisible\]** : valore booleano facoltativo che se impostato su `$true` rende immediatamente visibile lo strumento aggiuntivo nel riquadro degli strumenti associato.</span><span class="sxs-lookup"><span data-stu-id="82baa-114">**\[IsVisible\]** - optional Boolean If set to `$true`, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="82baa-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="82baa-115">Remove\( Item \)</span></span>

<span data-ttu-id="82baa-116">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="82baa-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="82baa-117">Rimuove lo strumento aggiuntivo specificato dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="82baa-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="82baa-118">**Item**: Microsoft.PowerShell.Host.ISE.ISEAddOnTool specifica l'oggetto che deve essere rimosso da Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="82baa-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="82baa-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="82baa-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="82baa-120">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="82baa-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="82baa-121">Seleziona la scheda di PowerShell specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="82baa-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="82baa-122">**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da selezionare.</span><span class="sxs-lookup"><span data-stu-id="82baa-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="82baa-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="82baa-123">Remove\( psTab \)</span></span>

<span data-ttu-id="82baa-124">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="82baa-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="82baa-125">Rimuove la scheda di PowerShell specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="82baa-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="82baa-126">**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="82baa-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="82baa-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="82baa-127">See Also</span></span>

- [<span data-ttu-id="82baa-128">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="82baa-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="82baa-129">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="82baa-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="82baa-130">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="82baa-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
