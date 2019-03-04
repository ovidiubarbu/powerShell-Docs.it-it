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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861407"
---
# <a name="defining-default-methods-for-objects"></a>Definizione dei metodi predefiniti per gli oggetti

Quando si estendono gli oggetti di .NET Framework, è possibile aggiungere metodi di codice e script per gli oggetti. Il codice XML che viene usato per definire questi metodi è descritto nelle sezioni seguenti.

> [!NOTE]
> Gli esempi nelle sezioni seguenti sono nel file di tipi Types.ps1xml nella directory di installazione di Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Metodi di codice

Un metodo di codice fa riferimento a un metodo statico di un oggetto .NET Framework.

Nell'esempio seguente, il **ConvertLargeIntegerToInt64** metodo viene aggiunto per il [XMLNode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo. Il [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento definisce il metodo esteso come un metodo del codice. Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome del metodo esteso. E, il [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) elemento specifica il metodo statico. (È anche possibile aggiungere il [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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

Un metodo di script definisce un metodo il cui valore è riportato l'output di uno script. Nell'esempio seguente, il **ConvertToDateTime** metodo viene aggiunto per il [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo. Il [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento definisce il metodo esteso come metodo di script. Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome del metodo esteso. E, il [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) elemento specifica lo script che genera il valore del metodo. (È anche possibile aggiungere il [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)

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