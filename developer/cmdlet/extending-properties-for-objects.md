---
title: Estensione delle proprietà per oggetti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068148"
---
# <a name="extending-properties-for-objects"></a>Estensione delle proprietà per gli oggetti

Quando si estendono gli oggetti di .NET Framework, è possibile aggiungere alias delle proprietà, le proprietà del codice, le proprietà di nota, proprietà di script e set di proprietà agli oggetti. Il codice XML che consente di definire queste proprietà è descritto nelle sezioni seguenti.

> [!NOTE]
> Gli esempi nelle sezioni seguenti sono nel file di tipi predefinito Types.ps1xml nella directory di installazione di Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Proprietà con alias

Una proprietà alias definisce un nuovo nome per una proprietà esistente.

Nell'esempio seguente, il `Count` proprietà viene aggiunta al [System. Array? Displayproperty = Fullname](/dotnet/api/System.Array) tipo. Il [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elemento definisce le proprietà estese come una proprietà alias. Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nuovo nome. E, il [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elemento specifica la proprietà esistente a cui fa riferimento l'alias. (È anche possibile aggiungere il [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

Nell'esempio seguente, il `Node` proprietà viene aggiunta al [DirectoryInfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo. Il [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento definisce le proprietà estese come una proprietà del codice. Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome della proprietà estesa. E, il [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elemento definisce il metodo statico che fa riferimento la proprietà estesa. (È anche possibile aggiungere il [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

## <a name="note-properties"></a>Proprietà di nota

Una proprietà di nota definisce una proprietà con un valore statico.

Nell'esempio seguente, il `Status` proprietà (il cui valore è sempre "Success") viene aggiunta al [DirectoryInfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo. Il [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento definisce le proprietà estese come proprietà di nota; la [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome della proprietà estesa; e il [valore](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Specifica il valore statico della proprietà estesa. (Il [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento può essere aggiunto anche ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

Una proprietà di script definisce una proprietà il cui valore è riportato l'output di uno script.

Nell'esempio seguente, il `VersionInfo` proprietà viene aggiunta al [FileInfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) tipo. Il [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento definisce le proprietà estese come proprietà di script. Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome della proprietà estesa. E, il [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento specifica lo script che genera il valore della proprietà. (È anche possibile aggiungere il [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

Un set di proprietà definisce un gruppo di proprietà estese che possono fare riferimento il nome del set. Ad esempio, il `Property` parametro del [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet è possibile specificare una proprietà specifica impostata da visualizzare. Quando viene specificato un set di proprietà, vengono visualizzate solo le proprietà che appartengono al set.

Non vi è alcuna restrizione sul numero di set di proprietà che possono essere definiti per un oggetto. Tuttavia, è necessario specificare il set di proprietà usate per definire le proprietà di visualizzazione predefinita di un oggetto all'interno del set di membri PSStandardMembers. Nel file Types.ps1xml tipi, i nomi di set di proprietà predefiniti includono DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet. Qualsiasi proprietà aggiuntiva che aggiungono al set di membri PSStandardMembers vengono ignorati.

Nell'esempio seguente, il set di proprietà DefaultDisplayPropertySet viene aggiunto al set di membri PSStandardMembers del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) tipo. Il [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento definisce il gruppo di proprietà. Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome del set di proprietà. E, il [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elemento specifica le proprietà del set. (È anche possibile aggiungere il [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento ai membri delle [tipo](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elemento.)

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

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
