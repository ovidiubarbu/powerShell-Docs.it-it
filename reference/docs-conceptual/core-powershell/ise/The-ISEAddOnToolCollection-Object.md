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
ms.locfileid: "30953056"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="de0dd-103">Oggetto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="de0dd-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="de0dd-104">L'oggetto **ISEAddOnToolCollection** è una raccolta di oggetti **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="de0dd-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="de0dd-105">Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.</span><span class="sxs-lookup"><span data-stu-id="de0dd-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="de0dd-106">Metodi</span><span class="sxs-lookup"><span data-stu-id="de0dd-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="de0dd-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="de0dd-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="de0dd-108">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="de0dd-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="de0dd-109">Aggiunge un nuovo strumento aggiuntivo alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="de0dd-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="de0dd-110">Restituisce lo strumento aggiuntivo appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="de0dd-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="de0dd-111">Prima di eseguire questo comando, è necessario installare lo strumento aggiuntivo nel computer locale e caricare l'assembly.</span><span class="sxs-lookup"><span data-stu-id="de0dd-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="de0dd-112">**Name**: la stringa specifica il nome visualizzato dello strumento aggiuntivo aggiunto a Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="de0dd-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="de0dd-113">**ControlType**: il tipo specifica il controllo aggiunto.</span><span class="sxs-lookup"><span data-stu-id="de0dd-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="de0dd-114">**\[IsVisible\]**: valore booleano facoltativo che se impostato su **$true** rende visibile lo strumento aggiuntivo nel riquadro associato degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="de0dd-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="de0dd-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="de0dd-115">Remove\( Item \)</span></span>

<span data-ttu-id="de0dd-116">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="de0dd-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="de0dd-117">Rimuove lo strumento aggiuntivo specificato dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="de0dd-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="de0dd-118">**Item**: Microsoft.PowerShell.Host.ISE.ISEAddOnTool specifica l'oggetto che deve essere rimosso da Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="de0dd-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="de0dd-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="de0dd-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="de0dd-120">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="de0dd-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="de0dd-121">Seleziona la scheda di PowerShell specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="de0dd-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="de0dd-122">**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da selezionare.</span><span class="sxs-lookup"><span data-stu-id="de0dd-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="de0dd-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="de0dd-123">Remove\( psTab \)</span></span>

<span data-ttu-id="de0dd-124">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="de0dd-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="de0dd-125">Rimuove la scheda di PowerShell specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="de0dd-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="de0dd-126">**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="de0dd-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="de0dd-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="de0dd-127">See Also</span></span>

- [<span data-ttu-id="de0dd-128">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="de0dd-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="de0dd-129">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="de0dd-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="de0dd-130">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="de0dd-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)