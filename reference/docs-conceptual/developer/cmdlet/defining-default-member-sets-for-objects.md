---
title: Definizione dei set di membri predefiniti per gli oggetti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369780"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="1fc37-102">Definizione dei set di membri predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="1fc37-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="1fc37-103">Il set di membri PSStandardMembers viene usato da Windows PowerShell per definire i set di proprietà predefiniti per un oggetto.</span><span class="sxs-lookup"><span data-stu-id="1fc37-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="1fc37-104">I set di proprietà predefiniti possono essere utilizzati da comandi quali i cmdlet di formattazione per visualizzare solo le proprietà definite dal set di proprietà.</span><span class="sxs-lookup"><span data-stu-id="1fc37-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="1fc37-105">I set di proprietà predefiniti includono DefaultDisplayProperty, DefaultDisplayPropertySet e DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="1fc37-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="1fc37-106">Windows PowerShell ignora tutti gli altri set di membri e altri set di proprietà aggiunti al set di membri PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="1fc37-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="1fc37-107">Set di membri per System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="1fc37-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="1fc37-108">Nell'esempio seguente, il set di membri PSStandardMembers definisce il set di proprietà DefaultDisplayPropertySet per gli oggetti [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="1fc37-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="1fc37-109">Questo set di proprietà viene usato dal cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="1fc37-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="1fc37-110">L'output seguente mostra le proprietà predefinite restituite dal cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="1fc37-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="1fc37-111">Per ogni oggetto processo vengono restituite solo le proprietà `Id`, `Handles`, `CPU` e `Name`.</span><span class="sxs-lookup"><span data-stu-id="1fc37-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1fc37-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1fc37-112">See Also</span></span>

[<span data-ttu-id="1fc37-113">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fc37-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
