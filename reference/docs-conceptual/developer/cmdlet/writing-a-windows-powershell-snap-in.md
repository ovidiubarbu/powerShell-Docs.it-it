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
ms.openlocfilehash: d12a66e354a23041fffb0f8fa286c849849ec2b0
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870473"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell

Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che può essere usato per registrare tutti i cmdlet e i provider di Windows PowerShell in un assembly.

Con questo tipo di snap-in non è possibile selezionare i cmdlet e i provider che si desidera registrare. Per scrivere uno snap-in che consente di selezionare quello registrato, vedere scrittura di [uno snap-in di Windows PowerShell personalizzato](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell

1. Aggiungere l'attributo RunInstallerAttribute.

2. Creare una classe pubblica che deriva dalla classe [System. Management. Automation. pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) .

    In questo esempio, il nome della classe è "GetProcPSSnapIn01".

3. Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio). Quando si denominano gli snap-in, non usare uno dei seguenti caratteri: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/``\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`

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

Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che può essere usato per registrare il cmdlet Get-proc nella shell di Windows PowerShell. Tenere presente che in questo esempio l'assembly completo conterrà solo la classe di snap-in GetProcPSSnapIn01 e la classe di cmdlet `Get-Proc`.

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

[Come registrare cmdlet, provider e applicazioni host](/previous-versions/ms714644(v=vs.85))

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
