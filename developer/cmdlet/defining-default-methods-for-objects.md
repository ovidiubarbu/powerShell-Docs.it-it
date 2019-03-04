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
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="b0eb9-102">Definizione dei metodi predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="b0eb9-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="b0eb9-103">Quando si estendono gli oggetti di .NET Framework, è possibile aggiungere metodi di codice e script per gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="b0eb9-104">Il codice XML che viene usato per definire questi metodi è descritto nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="b0eb9-105">Gli esempi nelle sezioni seguenti sono nel file di tipi Types.ps1xml nella directory di installazione di Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="b0eb9-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="b0eb9-106">Metodi di codice</span><span class="sxs-lookup"><span data-stu-id="b0eb9-106">Code Methods</span></span>

<span data-ttu-id="b0eb9-107">Un metodo di codice fa riferimento a un metodo statico di un oggetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="b0eb9-108">Nell'esempio seguente, il **ConvertLargeIntegerToInt64** metodo viene aggiunto per il [XMLNode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) tipo.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="b0eb9-109">Il [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento definisce il metodo esteso come un metodo del codice.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="b0eb9-110">Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome del metodo esteso.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="b0eb9-111">E, il [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) elemento specifica il metodo statico.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="b0eb9-112">(È anche possibile aggiungere il [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="b0eb9-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="b0eb9-113">Metodi di script</span><span class="sxs-lookup"><span data-stu-id="b0eb9-113">Script Methods</span></span>

<span data-ttu-id="b0eb9-114">Un metodo di script definisce un metodo il cui valore è riportato l'output di uno script.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="b0eb9-115">Nell'esempio seguente, il **ConvertToDateTime** metodo viene aggiunto per il [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) tipo.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="b0eb9-116">Il [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento definisce il metodo esteso come metodo di script.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="b0eb9-117">Il [nome](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elemento specifica il nome del metodo esteso.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="b0eb9-118">E, il [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) elemento specifica lo script che genera il valore del metodo.</span><span class="sxs-lookup"><span data-stu-id="b0eb9-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="b0eb9-119">(È anche possibile aggiungere il [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elemento ai membri delle [set di membri](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) elemento.)</span><span class="sxs-lookup"><span data-stu-id="b0eb9-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0eb9-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b0eb9-120">See Also</span></span>

[<span data-ttu-id="b0eb9-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0eb9-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)