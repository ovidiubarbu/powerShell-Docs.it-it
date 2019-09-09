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
# <a name="extending-properties-for-objects"></a><span data-ttu-id="81f8a-102">Estensione delle proprietà per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="81f8a-102">Extending Properties for Objects</span></span>

<span data-ttu-id="81f8a-103">Quando si estendono .NET Framework oggetti, è possibile aggiungere gli oggetti proprietà alias, proprietà del codice, nota proprietà, proprietà script e set di proprietà.</span><span class="sxs-lookup"><span data-stu-id="81f8a-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="81f8a-104">Il codice XML che definisce queste proprietà è descritto nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="81f8a-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="81f8a-105">Gli esempi nelle sezioni seguenti descrivono il file dei `Types.ps1xml` tipi predefiniti nella directory di installazione di PowerShell`$PSHOME`().</span><span class="sxs-lookup"><span data-stu-id="81f8a-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="81f8a-106">Per ulteriori informazioni, vedere [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="81f8a-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="81f8a-107">Proprietà alias</span><span class="sxs-lookup"><span data-stu-id="81f8a-107">Alias properties</span></span>

<span data-ttu-id="81f8a-108">Una proprietà alias definisce un nuovo nome per una proprietà esistente.</span><span class="sxs-lookup"><span data-stu-id="81f8a-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="81f8a-109">Nell'esempio seguente, la proprietà **count** viene aggiunta al tipo [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="81f8a-110">L'elemento [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) definisce la proprietà estesa come proprietà alias.</span><span class="sxs-lookup"><span data-stu-id="81f8a-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="81f8a-111">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nuovo nome.</span><span class="sxs-lookup"><span data-stu-id="81f8a-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="81f8a-112">L'elemento [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) specifica la proprietà esistente a cui fa riferimento l'alias.</span><span class="sxs-lookup"><span data-stu-id="81f8a-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="81f8a-113">È anche possibile aggiungere l' `AliasProperty` elemento ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="81f8a-114">Proprietà del codice</span><span class="sxs-lookup"><span data-stu-id="81f8a-114">Code properties</span></span>

<span data-ttu-id="81f8a-115">Una proprietà di codice fa riferimento a una proprietà statica di un oggetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81f8a-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="81f8a-116">Nell'esempio seguente viene aggiunta la proprietà **mode** al tipo [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="81f8a-117">L'elemento [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) definisce la proprietà estesa come proprietà del codice.</span><span class="sxs-lookup"><span data-stu-id="81f8a-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="81f8a-118">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="81f8a-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="81f8a-119">L'elemento [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) definisce il metodo statico a cui fa riferimento la proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="81f8a-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="81f8a-120">È anche possibile aggiungere l' `CodeProperty` elemento ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="81f8a-121">Note (proprietà)</span><span class="sxs-lookup"><span data-stu-id="81f8a-121">Note properties</span></span>

<span data-ttu-id="81f8a-122">Una proprietà nota definisce una proprietà con un valore statico.</span><span class="sxs-lookup"><span data-stu-id="81f8a-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="81f8a-123">Nell'esempio seguente, la proprietà **status** , il cui valore è sempre **Success**, viene aggiunta al tipo [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="81f8a-124">L'elemento [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) definisce la proprietà estesa come proprietà di nota.</span><span class="sxs-lookup"><span data-stu-id="81f8a-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="81f8a-125">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="81f8a-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="81f8a-126">L'elemento [value](/dotnet/api/system.management.automation.psnoteproperty.value) specifica il valore statico della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="81f8a-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="81f8a-127">L' `NoteProperty` elemento può anche essere aggiunto ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="81f8a-128">Proprietà script</span><span class="sxs-lookup"><span data-stu-id="81f8a-128">Script properties</span></span>

<span data-ttu-id="81f8a-129">Una proprietà di script definisce una proprietà il cui valore è l'output di uno script.</span><span class="sxs-lookup"><span data-stu-id="81f8a-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="81f8a-130">Nell'esempio seguente, la proprietà **VERSIONINFO** viene aggiunta al tipo [System. io. FileInfo](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="81f8a-131">L'elemento [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) definisce la proprietà estesa come proprietà di script.</span><span class="sxs-lookup"><span data-stu-id="81f8a-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="81f8a-132">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome della proprietà estesa.</span><span class="sxs-lookup"><span data-stu-id="81f8a-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="81f8a-133">L'elemento [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) specifica quindi lo script che genera il valore della proprietà.</span><span class="sxs-lookup"><span data-stu-id="81f8a-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="81f8a-134">È anche possibile aggiungere l' `ScriptProperty` elemento ai membri dell'elemento [risultanti](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="81f8a-135">Set di proprietà</span><span class="sxs-lookup"><span data-stu-id="81f8a-135">Property sets</span></span>

<span data-ttu-id="81f8a-136">Un set di proprietà definisce un gruppo di proprietà estese a cui è possibile fare riferimento tramite il nome del set.</span><span class="sxs-lookup"><span data-stu-id="81f8a-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="81f8a-137">Il parametro della**Proprietà** [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
, ad esempio, può specificare un set di proprietà specifico da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="81f8a-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="81f8a-138">Quando si specifica un set di proprietà, vengono visualizzate solo le proprietà che appartengono al set.</span><span class="sxs-lookup"><span data-stu-id="81f8a-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="81f8a-139">Non esiste alcuna restrizione al numero di set di proprietà che possono essere definiti per un oggetto.</span><span class="sxs-lookup"><span data-stu-id="81f8a-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="81f8a-140">Tuttavia, i set di proprietà utilizzati per definire le proprietà di visualizzazione predefinite di un oggetto devono essere specificati all'interno del set di membri **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="81f8a-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="81f8a-141">Nel file deitipi, i nomi predefiniti dei set di proprietà includono DefaultDisplayProperty, DefaultDisplayPropertySet e DefaultKeyPropertySet. `Types.ps1xml`</span><span class="sxs-lookup"><span data-stu-id="81f8a-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="81f8a-142">Eventuali set di proprietà aggiuntivi aggiunti al set di membri **PSStandardMembers** vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="81f8a-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="81f8a-143">Nell'esempio seguente, il set di proprietà **DefaultDisplayPropertySet** viene aggiunto al set di membri **PSStandardMembers** del tipo [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="81f8a-144">L'elemento [PropertySet](/dotnet/api/system.management.automation.pspropertyset) definisce il gruppo di proprietà.</span><span class="sxs-lookup"><span data-stu-id="81f8a-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="81f8a-145">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name) specifica il nome del set di proprietà.</span><span class="sxs-lookup"><span data-stu-id="81f8a-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="81f8a-146">L'elemento [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) specifica le proprietà del set.</span><span class="sxs-lookup"><span data-stu-id="81f8a-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="81f8a-147">È anche possibile aggiungere l' `PropertySet` elemento ai membri dell'elemento [Type](/dotnet/api/system.management.automation.pstypename) .</span><span class="sxs-lookup"><span data-stu-id="81f8a-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="81f8a-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="81f8a-148">See also</span></span>

[<span data-ttu-id="81f8a-149">Informazioni su types. ps1xml</span><span class="sxs-lookup"><span data-stu-id="81f8a-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="81f8a-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="81f8a-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="81f8a-151">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="81f8a-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
