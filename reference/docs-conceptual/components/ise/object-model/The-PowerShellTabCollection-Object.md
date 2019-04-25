---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086615"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="ec92f-103">Oggetto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="ec92f-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="ec92f-104">L'oggetto della raccolta **PowerShellTab** è una raccolta di oggetti **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="ec92f-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="ec92f-105">Ogni oggetto **PowerShellTab** funziona come un ambiente di runtime separato.</span><span class="sxs-lookup"><span data-stu-id="ec92f-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="ec92f-106">È un'istanza della classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="ec92f-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="ec92f-107">Un esempio è l'oggetto **$psISE.PowerShellTabs**.</span><span class="sxs-lookup"><span data-stu-id="ec92f-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ec92f-108">Metodi</span><span class="sxs-lookup"><span data-stu-id="ec92f-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="ec92f-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="ec92f-109">Add\(\)</span></span>

<span data-ttu-id="ec92f-110">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ec92f-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec92f-111">Aggiunge una nuova scheda di PowerShell alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="ec92f-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="ec92f-112">Restituisce la scheda appena aggiunta.</span><span class="sxs-lookup"><span data-stu-id="ec92f-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ec92f-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ec92f-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="ec92f-114">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ec92f-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec92f-115">Rimuove la scheda specificata dal parametro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="ec92f-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="ec92f-116">**psTab** Scheda di PowerShell da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="ec92f-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ec92f-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ec92f-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="ec92f-118">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="ec92f-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ec92f-119">Seleziona la scheda di PowerShell specificata dal parametro **psTab** in modo che diventi la scheda di PowerShell attualmente attiva.</span><span class="sxs-lookup"><span data-stu-id="ec92f-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="ec92f-120">**psTab** Scheda di PowerShell da selezionare.</span><span class="sxs-lookup"><span data-stu-id="ec92f-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec92f-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ec92f-121">See Also</span></span>

- [<span data-ttu-id="ec92f-122">Oggetto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ec92f-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="ec92f-123">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ec92f-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ec92f-124">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="ec92f-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)