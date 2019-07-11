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
# <a name="defining-default-methods-for-objects"></a>Definizione dei metodi predefiniti per gli oggetti

Quando si estendono gli oggetti di .NET Framework, è possibile aggiungere metodi di codice e script per gli oggetti. Il codice XML che viene usato per definire questi metodi è descritto nelle sezioni seguenti.

> [!NOTE]
> Gli esempi nelle sezioni seguenti sono nel file di tipi Types.ps1xml nella directory di installazione di Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Metodi di codice

Un metodo di codice fa riferimento a un metodo statico di un oggetto .NET Framework.

Nell'esempio seguente, il **ConvertLargeIntegerToInt64** metodo viene aggiunto per il [XMLNode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo. Il [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento definisce il metodo esteso come un metodo del codice. Il [nome](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento specifica il nome del metodo esteso. E, il [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elemento specifica il metodo statico. (È anche possibile aggiungere il [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elemento ai membri delle [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)

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

## <a name="script-methods"></a>Metodi di script

Un metodo di script definisce un metodo il cui valore è riportato l'output di uno script. Nell'esempio seguente, il **ConvertToDateTime** metodo viene aggiunto per il [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo. Il [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento definisce il metodo esteso come metodo di script. Il [nome](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elemento specifica il nome del metodo esteso. E, il [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elemento specifica lo script che genera il valore del metodo. (È anche possibile aggiungere il [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elemento ai membri delle [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) elemento.)

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

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
