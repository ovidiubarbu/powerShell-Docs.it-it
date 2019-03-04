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
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854527"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="f86ae-102">Estensione delle proprietà per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="f86ae-102">Extending Properties for Objects</span></span>

<span data-ttu-id="f86ae-103">Quando si estendono gli oggetti di .NET Framework, è possibile aggiungere alias delle proprietà, le proprietà del codice, le proprietà di nota, proprietà di script e set di proprietà agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="f86ae-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="f86ae-104">Il codice XML che consente di definire queste proprietà è descritto nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="f86ae-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="f86ae-105">Gli esempi nelle sezioni seguenti sono nel file di tipi predefinito Types.ps1xml nella directory di installazione di Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="f86ae-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="f86ae-106">Proprietà con alias</span><span class="sxs-lookup"><span data-stu-id="f86ae-106">Alias Properties</span></span>

<span data-ttu-id="f86ae-107">Una proprietà alias definisce un nuovo nome per una proprietà esistente.</span><span class="sxs-lookup"><span data-stu-id="f86ae-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="f86ae-108">Nell'esempio seguente, il `Count` proprietà viene aggiunta al [System. Array? Displayproperty = Fullname](/dotnet/api/System.Array) tipo.</span><span class="sxs-lookup"><span data-stu-id="f86ae-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="f86ae-109">Il [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) elemento definisce le proprietà estese come una proprietà alias.</span><span class="sxs-lookup"><span data-stu-id="f86ae-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="f86ae-110">Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nuovo nome.</span><span class="sxs-lookup"><span data-stu-id="f86ae-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="f86ae-111">E, il [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) elemento specifica la proprietà esistente a cui fa riferimento l'alias.</span><span class="sxs-lookup"><span data-stu-id="f86ae-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="f86ae-112">(È anche possibile aggiungere il [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="f86ae-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="f86ae-113">Proprietà del codice</span><span class="sxs-lookup"><span data-stu-id="f86ae-113">Code Properties</span></span>

<span data-ttu-id="f86ae-114">Una proprietà di codice fa riferimento a una proprietà statica di un oggetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f86ae-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="f86ae-115">Nell'esempio seguente, il `Node` proprietà viene aggiunta al [DirectoryInfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="f86ae-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="f86ae-116">Il [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento definisce le proprietà estese come una proprietà del codice.</span><span class="sxs-lookup"><span data-stu-id="f86ae-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="f86ae-117">Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="f86ae-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="f86ae-118">E, il [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) elemento definisce il metodo statico che fa riferimento la proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="f86ae-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="f86ae-119">(È anche possibile aggiungere il [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="f86ae-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="f86ae-120">Proprietà di nota</span><span class="sxs-lookup"><span data-stu-id="f86ae-120">Note Properties</span></span>

<span data-ttu-id="f86ae-121">Una proprietà di nota definisce una proprietà con un valore statico.</span><span class="sxs-lookup"><span data-stu-id="f86ae-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="f86ae-122">Nell'esempio seguente, il `Status` proprietà (il cui valore è sempre "Success") viene aggiunta al [DirectoryInfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="f86ae-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="f86ae-123">Il [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento definisce le proprietà estese come proprietà di nota; la [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome della proprietà estesa; e il [valore](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento Specifica il valore statico della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="f86ae-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="f86ae-124">(Il [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) elemento può essere aggiunto anche ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="f86ae-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="f86ae-125">Proprietà script</span><span class="sxs-lookup"><span data-stu-id="f86ae-125">Script Properties</span></span>

<span data-ttu-id="f86ae-126">Una proprietà di script definisce una proprietà il cui valore è riportato l'output di uno script.</span><span class="sxs-lookup"><span data-stu-id="f86ae-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="f86ae-127">Nell'esempio seguente, il `VersionInfo` proprietà viene aggiunta al [FileInfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) tipo.</span><span class="sxs-lookup"><span data-stu-id="f86ae-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="f86ae-128">Il [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento definisce le proprietà estese come proprietà di script.</span><span class="sxs-lookup"><span data-stu-id="f86ae-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="f86ae-129">Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="f86ae-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="f86ae-130">E, il [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) elemento specifica lo script che genera il valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="f86ae-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="f86ae-131">(È anche possibile aggiungere il [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="f86ae-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="f86ae-132">Set di proprietà</span><span class="sxs-lookup"><span data-stu-id="f86ae-132">Property Sets</span></span>

<span data-ttu-id="f86ae-133">Un set di proprietà definisce un gruppo di proprietà estese che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="f86ae-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="f86ae-134">Ad esempio, il `Property` parametro del [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet è possibile specificare una proprietà specifica impostata da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="f86ae-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="f86ae-135">Quando viene specificato un set di proprietà, vengono visualizzate solo le proprietà che appartengono al set.</span><span class="sxs-lookup"><span data-stu-id="f86ae-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="f86ae-136">Un set di proprietà definisce un gruppo di proprietà estese che possono fare riferimento il nome del set.</span><span class="sxs-lookup"><span data-stu-id="f86ae-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="f86ae-137">Ad esempio, il `Property` parametro del [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet è possibile specificare una proprietà specifica impostata da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="f86ae-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="f86ae-138">Quando viene specificato un set di proprietà, vengono visualizzate solo le proprietà che appartengono al set.</span><span class="sxs-lookup"><span data-stu-id="f86ae-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="f86ae-139">Non vi è alcuna restrizione sul numero di set di proprietà che possono essere definiti per un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f86ae-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="f86ae-140">Tuttavia, è necessario specificare il set di proprietà usate per definire le proprietà di visualizzazione predefinita di un oggetto all'interno del set di membri PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="f86ae-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="f86ae-141">Nel file Types.ps1xml tipi, i nomi di set di proprietà predefiniti includono DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="f86ae-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="f86ae-142">Qualsiasi proprietà aggiuntiva che aggiungono al set di membri PSStandardMembers vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="f86ae-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="f86ae-143">Nell'esempio seguente, il set di proprietà DefaultDisplayPropertySet viene aggiunto al set di membri PSStandardMembers del [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) tipo.</span><span class="sxs-lookup"><span data-stu-id="f86ae-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="f86ae-144">Il [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento definisce il gruppo di proprietà.</span><span class="sxs-lookup"><span data-stu-id="f86ae-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="f86ae-145">Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome del set di proprietà.</span><span class="sxs-lookup"><span data-stu-id="f86ae-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="f86ae-146">E, il [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) elemento specifica le proprietà del set.</span><span class="sxs-lookup"><span data-stu-id="f86ae-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="f86ae-147">(È anche possibile aggiungere il [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) elemento ai membri delle [tipo](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) elemento.)</span><span class="sxs-lookup"><span data-stu-id="f86ae-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f86ae-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f86ae-148">See Also</span></span>

[<span data-ttu-id="f86ae-149">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f86ae-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
