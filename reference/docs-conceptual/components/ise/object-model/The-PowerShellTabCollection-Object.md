---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto PowerShellTabCollection
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736114"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="83848-103">Oggetto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="83848-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="83848-104">L'oggetto della raccolta **PowerShellTab** è una raccolta di oggetti **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="83848-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="83848-105">Ogni oggetto **PowerShellTab** funziona come un ambiente di runtime separato.</span><span class="sxs-lookup"><span data-stu-id="83848-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="83848-106">È un'istanza della classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="83848-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="83848-107">Un esempio è l'oggetto `$psISE.PowerShellTabs`.</span><span class="sxs-lookup"><span data-stu-id="83848-107">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="83848-108">Metodi</span><span class="sxs-lookup"><span data-stu-id="83848-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="83848-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="83848-109">Add\(\)</span></span>

<span data-ttu-id="83848-110">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="83848-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83848-111">Aggiunge una nuova scheda di PowerShell alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="83848-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="83848-112">Restituisce la scheda appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="83848-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="83848-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="83848-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="83848-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="83848-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83848-115">Rimuove la scheda specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="83848-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="83848-116">**psTab** Scheda di PowerShell da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="83848-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="83848-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="83848-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="83848-118">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="83848-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83848-119">Seleziona la scheda di PowerShell specificata dal parametro **psTab** in modo che diventi la scheda di PowerShell attualmente attiva.</span><span class="sxs-lookup"><span data-stu-id="83848-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="83848-120">**psTab** Scheda di PowerShell da selezionare.</span><span class="sxs-lookup"><span data-stu-id="83848-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="83848-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="83848-121">See Also</span></span>

- [<span data-ttu-id="83848-122">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="83848-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="83848-123">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="83848-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="83848-124">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="83848-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
