---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Oggetto ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 33de866d706ec2b0894c5bfe49e07fee142b95c0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="eaba3-103">Oggetto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="eaba3-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="eaba3-104">Un oggetto **ISEMenuItem** è un'istanza della classe Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="eaba3-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="eaba3-105">Tutti gli oggetti nel menu **Componenti aggiuntivi** sono istanze della classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="eaba3-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="eaba3-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="eaba3-106">Properties</span></span>

###  <span data-ttu-id="eaba3-107"><a name="DisplayName"></a>DisplayName</span><span class="sxs-lookup"><span data-stu-id="eaba3-107"><a name="DisplayName"></a> DisplayName</span></span>
  <span data-ttu-id="eaba3-108">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eaba3-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eaba3-109">Proprietà di sola lettura che ottiene il nome visualizzato della voce di menu.</span><span class="sxs-lookup"><span data-stu-id="eaba3-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <span data-ttu-id="eaba3-110"><a name="Action"></a> Azione</span><span class="sxs-lookup"><span data-stu-id="eaba3-110"><a name="Action"></a> Action</span></span>
  <span data-ttu-id="eaba3-111">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eaba3-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eaba3-112">Proprietà di sola lettura che ottiene il blocco di script.</span><span class="sxs-lookup"><span data-stu-id="eaba3-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="eaba3-113">Richiama l'azione quando si sceglie la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="eaba3-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <span data-ttu-id="eaba3-114"><a name="Shortcut"></a> Shortcut</span><span class="sxs-lookup"><span data-stu-id="eaba3-114"><a name="Shortcut"></a> Shortcut</span></span>
  <span data-ttu-id="eaba3-115">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eaba3-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eaba3-116">Proprietà di sola lettura che ottiene il tasto di scelta rapida di input per la voce di menu.</span><span class="sxs-lookup"><span data-stu-id="eaba3-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <span data-ttu-id="eaba3-117"><a name="Submenus"></a> Sottomenu</span><span class="sxs-lookup"><span data-stu-id="eaba3-117"><a name="Submenus"></a> Submenus</span></span>
  <span data-ttu-id="eaba3-118">Supportato in Windows PowerShell ISE 2.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="eaba3-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="eaba3-119">Proprietà di sola lettura che ottiene l'[elenco di sottomenu](The-ISEMenuItemCollection-Object.md) della voce di menu.</span><span class="sxs-lookup"><span data-stu-id="eaba3-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="eaba3-120">Esempio di script</span><span class="sxs-lookup"><span data-stu-id="eaba3-120">Scripting example</span></span>
 <span data-ttu-id="eaba3-121">Per comprendere meglio l'utilizzo del menu Componenti aggiuntivi e le relative proprietà gestibili tramite script, vedere l'esempio di script seguente.</span><span class="sxs-lookup"><span data-stu-id="eaba3-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="eaba3-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eaba3-122">See Also</span></span>
- [<span data-ttu-id="eaba3-123">Oggetto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="eaba3-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="eaba3-124">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eaba3-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="eaba3-125">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eaba3-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="eaba3-126">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="eaba3-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
