---
title: Definizione dei metodi predefiniti per gli oggetti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215282"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="a0654-102">Definizione dei metodi predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="a0654-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="a0654-103">Quando si estendono .NET Framework oggetti, è possibile aggiungere metodi di codice e metodi di script agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="a0654-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="a0654-104">Il codice XML utilizzato per definire questi metodi è descritto nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="a0654-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="a0654-105">Gli esempi nelle sezioni seguenti si trovano nel file `Types.ps1xml` dei tipi nella directory di installazione di Windows PowerShell`$PSHOME`().</span><span class="sxs-lookup"><span data-stu-id="a0654-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="a0654-106">Per ulteriori informazioni, vedere [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="a0654-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="a0654-107">Metodi di codice</span><span class="sxs-lookup"><span data-stu-id="a0654-107">Code methods</span></span>

<span data-ttu-id="a0654-108">Un metodo di codice fa riferimento a un metodo statico di un oggetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0654-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="a0654-109">Nell'esempio seguente viene aggiunto il metodo **ToString** al tipo [System. XML. XMLNode](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="a0654-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="a0654-110">L'elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) definisce il metodo esteso come metodo di codice.</span><span class="sxs-lookup"><span data-stu-id="a0654-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="a0654-111">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) specifica il nome del metodo esteso.</span><span class="sxs-lookup"><span data-stu-id="a0654-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="a0654-112">E, l'elemento [codereference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) specifica il metodo statico.</span><span class="sxs-lookup"><span data-stu-id="a0654-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="a0654-113">È anche possibile aggiungere l'elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) ai membri dell'elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="a0654-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="a0654-114">Metodi di script</span><span class="sxs-lookup"><span data-stu-id="a0654-114">Script methods</span></span>

<span data-ttu-id="a0654-115">Un metodo di script definisce un metodo il cui valore è l'output di uno script.</span><span class="sxs-lookup"><span data-stu-id="a0654-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="a0654-116">Nell'esempio seguente viene aggiunto il metodo **ConvertToDateTime** al tipo [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="a0654-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="a0654-117">L'elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) definisce il metodo esteso come metodo di script.</span><span class="sxs-lookup"><span data-stu-id="a0654-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="a0654-118">L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) specifica il nome del metodo esteso.</span><span class="sxs-lookup"><span data-stu-id="a0654-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="a0654-119">L'elemento [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) specifica quindi lo script che genera il valore del metodo.</span><span class="sxs-lookup"><span data-stu-id="a0654-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="a0654-120">È anche possibile aggiungere l'elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) ai membri dell'elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="a0654-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="a0654-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a0654-121">See also</span></span>

[<span data-ttu-id="a0654-122">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0654-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
