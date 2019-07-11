---
title: Definizione di metodi predefiniti per gli oggetti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733988"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="13ee5-102">Definizione dei metodi predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="13ee5-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="13ee5-103">Quando si estendono gli oggetti di .NET Framework, è possibile aggiungere metodi di codice e script per gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="13ee5-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="13ee5-104">Il codice XML che viene usato per definire questi metodi è descritto nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="13ee5-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="13ee5-105">Gli esempi nelle sezioni seguenti sono nel file di tipi Types.ps1xml nella directory di installazione di Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="13ee5-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="13ee5-106">Metodi di codice</span><span class="sxs-lookup"><span data-stu-id="13ee5-106">Code Methods</span></span>

<span data-ttu-id="13ee5-107">Un metodo di codice fa riferimento a un metodo statico di un oggetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13ee5-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="13ee5-108">Nell'esempio seguente, il **ConvertLargeIntegerToInt64** metodo viene aggiunto per il [XMLNode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo.</span><span class="sxs-lookup"><span data-stu-id="13ee5-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="13ee5-109">Il [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento definisce il metodo esteso come un metodo del codice.</span><span class="sxs-lookup"><span data-stu-id="13ee5-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="13ee5-110">Il [nome](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento specifica il nome del metodo esteso.</span><span class="sxs-lookup"><span data-stu-id="13ee5-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="13ee5-111">E, il [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elemento specifica il metodo statico.</span><span class="sxs-lookup"><span data-stu-id="13ee5-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="13ee5-112">(È anche possibile aggiungere il [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento ai membri delle [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)</span><span class="sxs-lookup"><span data-stu-id="13ee5-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="13ee5-113">Metodi di script</span><span class="sxs-lookup"><span data-stu-id="13ee5-113">Script Methods</span></span>

<span data-ttu-id="13ee5-114">Un metodo di script definisce un metodo il cui valore è riportato l'output di uno script.</span><span class="sxs-lookup"><span data-stu-id="13ee5-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="13ee5-115">Nell'esempio seguente, il **ConvertToDateTime** metodo viene aggiunto per il [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo.</span><span class="sxs-lookup"><span data-stu-id="13ee5-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="13ee5-116">Il [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento definisce il metodo esteso come metodo di script.</span><span class="sxs-lookup"><span data-stu-id="13ee5-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="13ee5-117">Il [nome](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento specifica il nome del metodo esteso.</span><span class="sxs-lookup"><span data-stu-id="13ee5-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="13ee5-118">E, il [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elemento specifica lo script che genera il valore del metodo.</span><span class="sxs-lookup"><span data-stu-id="13ee5-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="13ee5-119">(È anche possibile aggiungere il [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento ai membri delle [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)</span><span class="sxs-lookup"><span data-stu-id="13ee5-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="13ee5-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="13ee5-120">See Also</span></span>

[<span data-ttu-id="13ee5-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="13ee5-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
