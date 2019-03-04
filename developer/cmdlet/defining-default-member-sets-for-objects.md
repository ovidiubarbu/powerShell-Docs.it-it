---
title: La definizione di set di membri predefinito per gli oggetti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859797"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="a3e28-102">Definizione dei set di membri predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="a3e28-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="a3e28-103">Il set di membri PSStandardMembers viene utilizzato da Windows PowerShell per definire i set di proprietà predefinito per un oggetto.</span><span class="sxs-lookup"><span data-stu-id="a3e28-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="a3e28-104">I set di proprietà predefiniti sono utilizzabile dai comandi, ad esempio i cmdlet di formattazione per visualizzare solo le proprietà definite dal set di proprietà.</span><span class="sxs-lookup"><span data-stu-id="a3e28-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="a3e28-105">I set di proprietà predefiniti includono DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="a3e28-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="a3e28-106">Windows PowerShell ignora tutti gli altri set di membri e qualsiasi altro set di proprietà aggiunte al set di membri PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="a3e28-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="a3e28-107">Set di membri per Diagnostics</span><span class="sxs-lookup"><span data-stu-id="a3e28-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="a3e28-108">Nell'esempio seguente, il set di membri PSStandardMembers definisce la proprietà DefaultDisplayPropertySet impostata per [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetti.</span><span class="sxs-lookup"><span data-stu-id="a3e28-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="a3e28-109">Questo set di proprietà viene utilizzato per la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e28-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="a3e28-110">Nell'esempio seguente, il set di membri PSStandardMembers definisce la proprietà DefaultDisplayPropertySet impostata per [Diagnostics](/dotnet/api/System.Diagnostics.Process) oggetti.</span><span class="sxs-lookup"><span data-stu-id="a3e28-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="a3e28-111">Questo set di proprietà viene utilizzato per la [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e28-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

<span data-ttu-id="a3e28-112">L'output seguente mostra le proprietà predefinite restituite dai [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e28-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="a3e28-113">Solo le `Id`, `Handles`, `CPU`, e `Name` proprietà restituite per ogni oggetto processo.</span><span class="sxs-lookup"><span data-stu-id="a3e28-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="a3e28-114">L'output seguente mostra le proprietà predefinite restituite dai [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3e28-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="a3e28-115">Solo le `Id`, `Handles`, `CPU`, e `Name` proprietà restituite per ogni oggetto processo.</span><span class="sxs-lookup"><span data-stu-id="a3e28-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a><span data-ttu-id="a3e28-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a3e28-116">See Also</span></span>

[<span data-ttu-id="a3e28-117">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3e28-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
