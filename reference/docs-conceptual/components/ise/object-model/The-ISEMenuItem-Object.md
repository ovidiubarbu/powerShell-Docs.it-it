---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Oggetto ISEMenuItem
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736982"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="1cf78-103">Oggetto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="1cf78-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="1cf78-104">Un oggetto **ISEMenuItem** è un'istanza della classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="1cf78-104">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="1cf78-105">Tutti gli oggetti nel menu **Componenti aggiuntivi** sono istanze della classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="1cf78-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="1cf78-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="1cf78-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="1cf78-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1cf78-107">DisplayName</span></span>

<span data-ttu-id="1cf78-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="1cf78-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1cf78-109">Proprietà di sola lettura che ottiene il nome visualizzato della voce di menu.</span><span class="sxs-lookup"><span data-stu-id="1cf78-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="1cf78-110">Azione</span><span class="sxs-lookup"><span data-stu-id="1cf78-110">Action</span></span>

<span data-ttu-id="1cf78-111">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="1cf78-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1cf78-112">Proprietà di sola lettura che ottiene il blocco di script.</span><span class="sxs-lookup"><span data-stu-id="1cf78-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="1cf78-113">Richiama l'azione quando si sceglie la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="1cf78-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="1cf78-114">Tasto di scelta rapida</span><span class="sxs-lookup"><span data-stu-id="1cf78-114">Shortcut</span></span>

<span data-ttu-id="1cf78-115">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="1cf78-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1cf78-116">Proprietà di sola lettura che ottiene il tasto di scelta rapida di input per la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="1cf78-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="1cf78-117">Sottomenu</span><span class="sxs-lookup"><span data-stu-id="1cf78-117">Submenus</span></span>

<span data-ttu-id="1cf78-118">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="1cf78-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="1cf78-119">Proprietà di sola lettura che ottiene l'[elenco di sottomenu](The-ISEMenuItemCollection-Object.md) della voce di menu.</span><span class="sxs-lookup"><span data-stu-id="1cf78-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="1cf78-120">Esempio di script</span><span class="sxs-lookup"><span data-stu-id="1cf78-120">Scripting example</span></span>

<span data-ttu-id="1cf78-121">Per comprendere meglio l'utilizzo del menu Componenti aggiuntivi e le relative proprietà gestibili tramite script, vedere l'esempio di script seguente.</span><span class="sxs-lookup"><span data-stu-id="1cf78-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="1cf78-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1cf78-122">See Also</span></span>

- [<span data-ttu-id="1cf78-123">Oggetto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="1cf78-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="1cf78-124">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1cf78-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1cf78-125">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="1cf78-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
