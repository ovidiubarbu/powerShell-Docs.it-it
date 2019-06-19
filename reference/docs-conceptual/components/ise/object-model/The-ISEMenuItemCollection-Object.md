---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Oggetto ISEMenuItemCollection
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030535"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="69d59-103">Oggetto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="69d59-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="69d59-104">Un oggetto **ISEMenuItemCollection** è una raccolta di oggetti **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="69d59-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="69d59-105">È un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="69d59-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="69d59-106">Un esempio è l'oggetto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**, usato per personalizzare il menu **Componenti aggiuntivi** in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="69d59-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="69d59-107">Metodo</span><span class="sxs-lookup"><span data-stu-id="69d59-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="69d59-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="69d59-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="69d59-109">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="69d59-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="69d59-110">Aggiunge una voce di menu alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="69d59-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="69d59-111">**DisplayName** Nome visualizzato del menu da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="69d59-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="69d59-112">**Action** Oggetto **System.Management.Automation.ScriptBlock** che specifica l'azione associata alla voce di menu.</span><span class="sxs-lookup"><span data-stu-id="69d59-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="69d59-113">**Shortcut** Tasto di scelta rapida per l'azione.</span><span class="sxs-lookup"><span data-stu-id="69d59-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="69d59-114">**Returns** Oggetto ISEMenuItem appena aggiunto.</span><span class="sxs-lookup"><span data-stu-id="69d59-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="69d59-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="69d59-115">Clear\(\)</span></span>

<span data-ttu-id="69d59-116">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="69d59-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="69d59-117">Rimuove tutti i sottomenu dalla voce di menu.</span><span class="sxs-lookup"><span data-stu-id="69d59-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="69d59-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69d59-118">See Also</span></span>

- [<span data-ttu-id="69d59-119">Oggetto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="69d59-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="69d59-120">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="69d59-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="69d59-121">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="69d59-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
