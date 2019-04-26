---
title: La scrittura di uno Snap-in PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066958"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell

In questo esempio viene illustrato come scrivere uno snap-in Windows PowerShell che può essere utilizzato per registrare tutti i cmdlet e provider Windows PowerShell in un assembly.

Con questo tipo di snap-in, non si seleziona quali cmdlet e provider che si desidera registrare. Per scrivere uno snap-in che modo è possibile selezionare quello registrato, vedere [scrivere uno Snap-in PowerShell di Windows personalizzate](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell

1. Aggiungere l'attributo RunInstallerAttribute.

2. Creare una classe pubblica che deriva dal [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) classe.

    In questo esempio, il nome della classe è "GetProcPSSnapIn01".

3. Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio). Quando si rinomina gli snap-in, non usare uno qualsiasi dei seguenti caratteri: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    In questo esempio, il nome dello snap-in è "GetProcPSSnapIn01".

4. Aggiungere una proprietà pubblica del fornitore dello snap-in (obbligatorio).

    In questo esempio, il fornitore è "Microsoft".

5. Aggiungere una proprietà pubblica per la risorsa di fornitore dello snap-in (facoltativo).

    In questo esempio, la risorsa di fornitore è "GetProcPSSnapIn01, Microsoft".

6. Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).

    In questo esempio, la descrizione è "This is uno snap-in Windows PowerShell che registra il cmdlet get-Process".

7. Aggiungere una proprietà pubblica per la risorsa di descrizione dello snap-in (facoltativo).

    In questo esempio, la risorsa di fornitore è "GetProcPSSnapIn01, questo è uno snap-in Windows PowerShell che registra il cmdlet get-Process".

## <a name="example"></a>Esempio

In questo esempio viene illustrato come scrivere uno snap-in Windows PowerShell che può essere utilizzato per registrare il cmdlet Get-Process nella shell di Windows PowerShell. Tenere presente che in questo esempio, l'assembly completo conterrà solo la GetProcPSSnapIn01 snap-in di classe e la classe del cmdlet Get-Process.

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a>Vedere anche

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
