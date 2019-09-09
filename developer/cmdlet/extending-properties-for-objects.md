---
title: Estensione delle proprietà per gli oggetti | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986483"
---
# <a name="extending-properties-for-objects"></a>Estensione delle proprietà per gli oggetti

Quando si estendono .NET Framework oggetti, è possibile aggiungere gli oggetti proprietà alias, proprietà del codice, nota proprietà, proprietà script e set di proprietà. Il codice XML che definisce queste proprietà è descritto nelle sezioni seguenti.

> [!NOTE]
> Gli esempi nelle sezioni seguenti descrivono il file dei `Types.ps1xml` tipi predefiniti nella directory di installazione di PowerShell`$PSHOME`(). Per ulteriori informazioni, vedere [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Proprietà alias

Una proprietà alias definisce un nuovo nome per una proprietà esistente.

Nell'esempio seguente, la proprietà **count** viene aggiunta al tipo [System. Array](/dotnet/api/System.Array) . L'elemento [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) definisce la proprietà estesa come proprietà alias. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nuovo nome. L'elemento [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) specifica la proprietà esistente a cui fa riferimento l'alias. È anche possibile aggiungere l' `AliasProperty` elemento ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a>Proprietà del codice

Una proprietà di codice fa riferimento a una proprietà statica di un oggetto .NET Framework.

Nell'esempio seguente viene aggiunta la proprietà **mode** al tipo [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . L'elemento [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) definisce la proprietà estesa come proprietà del codice. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome della proprietà estesa. L'elemento [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) definisce il metodo statico a cui fa riferimento la proprietà estesa. È anche possibile aggiungere l' `CodeProperty` elemento ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a>Note (proprietà)

Una proprietà nota definisce una proprietà con un valore statico.

Nell'esempio seguente, la proprietà **status** , il cui valore è sempre **Success**, viene aggiunta al tipo [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . L'elemento [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) definisce la proprietà estesa come proprietà di nota. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome della proprietà estesa. L'elemento [value](/dotnet/api/system.management.automation.psnoteproperty.value) specifica il valore statico della proprietà estesa. L' `NoteProperty` elemento può anche essere aggiunto ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a>Proprietà script

Una proprietà di script definisce una proprietà il cui valore è l'output di uno script.

Nell'esempio seguente, la proprietà **VERSIONINFO** viene aggiunta al tipo [System. io. FileInfo](/dotnet/api/System.IO.FileInfo) . L'elemento [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) definisce la proprietà estesa come proprietà di script. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome della proprietà estesa. L'elemento [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) specifica quindi lo script che genera il valore della proprietà. È anche possibile aggiungere l' `ScriptProperty` elemento ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a>Set di proprietà

Un set di proprietà definisce un gruppo di proprietà estese a cui è possibile fare riferimento tramite il nome del set.
Il parametro della**Proprietà** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
, ad esempio, può specificare un set di proprietà specifico da visualizzare. Quando si specifica un set di proprietà, vengono visualizzate solo le proprietà che appartengono al set.

Non esiste alcuna restrizione al numero di set di proprietà che possono essere definiti per un oggetto. Tuttavia, i set di proprietà utilizzati per definire le proprietà di visualizzazione predefinite di un oggetto devono essere specificati all'interno del set di membri **PSStandardMembers** . Nel file deitipi, i nomi predefiniti dei set di proprietà includono DefaultDisplayProperty, DefaultDisplayPropertySet e DefaultKeyPropertySet. `Types.ps1xml` Eventuali set di proprietà aggiuntivi aggiunti al set di membri **PSStandardMembers** vengono ignorati.

Nell'esempio seguente, il set di proprietà **DefaultDisplayPropertySet** viene aggiunto al set di membri **PSStandardMembers** del tipo [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) . L'elemento [PropertySet](/dotnet/api/system.management.automation.pspropertyset) definisce il gruppo di proprietà. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome del set di proprietà. L'elemento [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) specifica le proprietà del set. È anche possibile aggiungere l' `PropertySet` elemento ai membri dell'elemento [Type](/dotnet/api/system.management.automation.pstypename) .

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a>Vedere anche

[Informazioni su types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
