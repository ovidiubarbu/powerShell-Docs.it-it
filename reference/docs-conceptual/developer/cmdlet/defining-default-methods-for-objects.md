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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365690"
---
# <a name="defining-default-methods-for-objects"></a>Definizione dei metodi predefiniti per gli oggetti

Quando si estendono .NET Framework oggetti, è possibile aggiungere metodi di codice e metodi di script agli oggetti.
Il codice XML utilizzato per definire questi metodi è descritto nelle sezioni seguenti.

> [!NOTE]
> Gli esempi nelle sezioni seguenti si riportano dal file di tipi `Types.ps1xml` nella directory di installazione di Windows PowerShell (`$PSHOME`). Per ulteriori informazioni, vedere [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Metodi di codice

Un metodo di codice fa riferimento a un metodo statico di un oggetto .NET Framework.

Nell'esempio seguente viene aggiunto il metodo **ToString** al tipo [System. XML. XMLNode](/dotnet/api/System.Xml.XmlNode) . L'elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) definisce il metodo esteso come metodo di codice. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) specifica il nome del metodo esteso. E, l'elemento [codereference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) specifica il metodo statico. È anche possibile aggiungere l'elemento [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) ai membri dell'elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

## <a name="script-methods"></a>Metodi di script

Un metodo di script definisce un metodo il cui valore è l'output di uno script. Nell'esempio seguente viene aggiunto il metodo **ConvertToDateTime** al tipo [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . L'elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) definisce il metodo esteso come metodo di script. L'elemento [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) specifica il nome del metodo esteso. L'elemento [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) specifica quindi lo script che genera il valore del metodo. È anche possibile aggiungere l'elemento [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) ai membri dell'elemento [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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
