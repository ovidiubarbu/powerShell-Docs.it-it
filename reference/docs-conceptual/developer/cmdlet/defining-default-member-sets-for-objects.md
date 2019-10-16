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
# <a name="defining-default-member-sets-for-objects"></a>Definizione dei set di membri predefiniti per gli oggetti

Il set di membri PSStandardMembers viene usato da Windows PowerShell per definire i set di proprietà predefiniti per un oggetto. I set di proprietà predefiniti possono essere utilizzati da comandi quali i cmdlet di formattazione per visualizzare solo le proprietà definite dal set di proprietà. I set di proprietà predefiniti includono DefaultDisplayProperty, DefaultDisplayPropertySet e DefaultKeyPropertySet. Windows PowerShell ignora tutti gli altri set di membri e altri set di proprietà aggiunti al set di membri PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Set di membri per System. Diagnostics. Process

Nell'esempio seguente, il set di membri PSStandardMembers definisce il set di proprietà DefaultDisplayPropertySet per gli oggetti [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) . Questo set di proprietà viene usato dal cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .

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

L'output seguente mostra le proprietà predefinite restituite dal cmdlet [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) . Per ogni oggetto processo vengono restituite solo le proprietà `Id`, `Handles`, `CPU` e `Name`.

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

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
