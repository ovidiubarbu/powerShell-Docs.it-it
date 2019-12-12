---
title: Scrittura di uno snap-in di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 465ab9e8fa29716ce0f46ad0dcf01d0ddd615bcd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364230"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell

Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che può essere usato per registrare tutti i cmdlet e i provider di Windows PowerShell in un assembly.

Con questo tipo di snap-in non è possibile selezionare i cmdlet e i provider che si desidera registrare. Per scrivere uno snap-in che consente di selezionare quello registrato, vedere scrittura di [uno snap-in di Windows PowerShell personalizzato](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell

1. Aggiungere l'attributo RunInstallerAttribute.

2. Creare una classe pubblica che deriva dalla classe [System. Management. Automation. pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) .

    In questo esempio, il nome della classe è "GetProcPSSnapIn01".

3. Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio). Quando si assegnano nomi agli snap-in, non usare i caratteri seguenti: #. , () {} [] &-/\ $; : "' \< >;? @ ` *

    In questo esempio, il nome dello snap-in è "GetProcPSSnapIn01".

4. Aggiungere una proprietà pubblica per il fornitore dello snap-in (obbligatorio).

    In questo esempio, il fornitore è "Microsoft".

5. Aggiungere una proprietà pubblica per la risorsa fornitore dello snap-in (facoltativo).

    In questo esempio, la risorsa fornitore è "GetProcPSSnapIn01, Microsoft".

6. Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).

    In questo esempio, la descrizione è "questo è uno snap-in di Windows PowerShell che registra il cmdlet Get-proc".

7. Aggiungere una proprietà pubblica per la risorsa Description dello snap-in (facoltativo).

    In questo esempio, la risorsa fornitore è "GetProcPSSnapIn01, questo è uno snap-in di Windows PowerShell che registra il cmdlet Get-proc".

## <a name="example"></a>Esempio

Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che può essere usato per registrare il cmdlet Get-proc nella shell di Windows PowerShell. Tenere presente che in questo esempio l'assembly completo conterrà solo la classe di snap-in GetProcPSSnapIn01 e la classe del cmdlet Get-proc.

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

[Come registrare cmdlet, provider e applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
