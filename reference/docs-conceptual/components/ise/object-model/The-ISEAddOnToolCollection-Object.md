---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEAddOnToolCollection
ms.openlocfilehash: 28ab9747e573b7a76ee655289b341870b1728bc2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030615"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="9789b-103">Oggetto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="9789b-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="9789b-104">L'oggetto **ISEAddOnToolCollection** è una raccolta di oggetti **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="9789b-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="9789b-105">Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.</span><span class="sxs-lookup"><span data-stu-id="9789b-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="9789b-106">Metodi</span><span class="sxs-lookup"><span data-stu-id="9789b-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="9789b-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="9789b-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="9789b-108">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="9789b-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9789b-109">Aggiunge un nuovo strumento aggiuntivo alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="9789b-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="9789b-110">Restituisce lo strumento aggiuntivo appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="9789b-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="9789b-111">Prima di eseguire questo comando, è necessario installare lo strumento aggiuntivo nel computer locale e caricare l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9789b-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="9789b-112">**Name**: la stringa specifica il nome visualizzato dello strumento aggiuntivo aggiunto a Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9789b-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="9789b-113">**ControlType**: il tipo specifica il controllo aggiunto.</span><span class="sxs-lookup"><span data-stu-id="9789b-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="9789b-114">**\[IsVisible\]** : valore booleano facoltativo che se impostato su **$true** rende visibile lo strumento aggiuntivo nel riquadro associato degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="9789b-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="9789b-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="9789b-115">Remove\( Item \)</span></span>

<span data-ttu-id="9789b-116">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="9789b-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9789b-117">Rimuove lo strumento aggiuntivo specificato dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="9789b-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="9789b-118">**Item**: Microsoft.PowerShell.Host.ISE.ISEAddOnTool specifica l'oggetto che deve essere rimosso da Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9789b-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="9789b-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="9789b-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="9789b-120">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="9789b-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9789b-121">Seleziona la scheda di PowerShell specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="9789b-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="9789b-122">**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da selezionare.</span><span class="sxs-lookup"><span data-stu-id="9789b-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="9789b-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="9789b-123">Remove\( psTab \)</span></span>

<span data-ttu-id="9789b-124">Supportato in Windows PowerShell ISE 3.0 e versioni successive e non presente nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="9789b-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9789b-125">Rimuove la scheda di PowerShell specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="9789b-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="9789b-126">**psTab**: Microsoft.PowerShell.Host.ISE.PowerShellTab indica la scheda di PowerShell da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="9789b-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="9789b-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9789b-127">See Also</span></span>

- [<span data-ttu-id="9789b-128">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="9789b-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="9789b-129">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9789b-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9789b-130">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="9789b-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
