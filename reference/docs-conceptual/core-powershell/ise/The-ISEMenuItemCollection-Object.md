---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="b86d0-103">Oggetto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="b86d0-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="b86d0-104">Un oggetto **ISEMenuItemCollection** è una raccolta di oggetti **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="b86d0-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="b86d0-105">È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="b86d0-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="b86d0-106">Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**, usato per personalizzare il menu **Componenti aggiuntivi** in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="b86d0-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="b86d0-107">Metodo</span><span class="sxs-lookup"><span data-stu-id="b86d0-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="b86d0-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="b86d0-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="b86d0-109">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b86d0-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b86d0-110">Aggiunge una voce di menu alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="b86d0-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="b86d0-111">**DisplayName** Nome visualizzato del menu da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="b86d0-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="b86d0-112">**Action** Oggetto **System.Management.Automation.ScriptBlock** che specifica l'azione associata alla voce di menu.</span><span class="sxs-lookup"><span data-stu-id="b86d0-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="b86d0-113">**Shortcut** Tasto di scelta rapida per l'azione.</span><span class="sxs-lookup"><span data-stu-id="b86d0-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="b86d0-114">**Returns** Oggetto ISEMenuItem appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="b86d0-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="b86d0-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="b86d0-115">Clear\(\)</span></span>

<span data-ttu-id="b86d0-116">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b86d0-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b86d0-117">Rimuove tutti i sottomenu dalla voce di menu.</span><span class="sxs-lookup"><span data-stu-id="b86d0-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="b86d0-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b86d0-118">See Also</span></span>

- [<span data-ttu-id="b86d0-119">Oggetto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="b86d0-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="b86d0-120">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b86d0-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b86d0-121">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="b86d0-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)