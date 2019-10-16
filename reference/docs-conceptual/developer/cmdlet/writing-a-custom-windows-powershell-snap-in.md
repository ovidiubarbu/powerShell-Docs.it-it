---
title: Scrittura di uno snap-in di Windows PowerShell personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364250"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell personalizzato

Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che registra cmdlet specifici.

Con questo tipo di snap-in è possibile specificare i cmdlet, i provider, i tipi o i formati da registrare. Per ulteriori informazioni sulla scrittura di uno snap-in che registra tutti i cmdlet e i provider in un assembly, vedere [scrittura di uno snap-in di Windows PowerShell](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Per scrivere uno snap-in di Windows PowerShell che registra cmdlet specifici.

1. Aggiungere l'attributo RunInstallerAttribute.

2. Creare una classe pubblica che deriva dalla classe [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

   In questo esempio, il nome della classe è "CustomPSSnapinTest".

3. Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio). Quando si assegnano nomi agli snap-in, non usare i caratteri seguenti: #. , () {} [] &-/\ $; : "' \< > &#124; ? @ ` *

   In questo esempio, il nome dello snap-in è "CustomPSSnapInTest".

4. Aggiungere una proprietà pubblica per il fornitore dello snap-in (obbligatorio).

   In questo esempio, il fornitore è "Microsoft".

5. Aggiungere una proprietà pubblica per la risorsa fornitore dello snap-in (facoltativo).

   In questo esempio, la risorsa fornitore è "CustomPSSnapInTest, Microsoft".

6. Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).

   In questo esempio la descrizione è: "si tratta di uno snap-in di Windows PowerShell personalizzato che include i cmdlet test-HelloWorld e test-CustomSnapinTest".

7. Aggiungere una proprietà pubblica per la risorsa Description dello snap-in (facoltativo).

   In questo esempio, la risorsa fornitore è "CustomPSSnapInTest", si tratta di uno snap-in di Windows PowerShell personalizzato che include i cmdlet test-HelloWorld e test-CustomSnapinTest ".

8. Specificare i cmdlet che appartengono allo snap-in personalizzato (facoltativo) utilizzando la classe [System. Management. Automation. Runspaces. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) . Le informazioni aggiunte includono il nome del cmdlet, il tipo .NET e il nome del file della guida del cmdlet. il formato del nome del file della guida del cmdlet deve essere Name. dll-help. XML.

   Questo esempio aggiunge i cmdlet test-HelloWorld e TestCustomSnapinTest.

9. Specificare i provider che appartengono allo snap-in personalizzato (facoltativo).

   Questo esempio non specifica alcun provider.

10. Specificare i tipi che appartengono allo snap-in personalizzato (facoltativo).

    In questo esempio non vengono specificati tipi.

11. Specificare i formati che appartengono allo snap-in personalizzato (facoltativo).

    In questo esempio non viene specificato alcun formato.

## <a name="example"></a>Esempio

Questo esempio illustra come scrivere uno snap-in di Windows PowerShell personalizzato che può essere usato per registrare i cmdlet test-HelloWorld e test-CustomSnapinTest. Tenere presente che in questo esempio l'assembly completo potrebbe contenere altri cmdlet e provider che non sarebbero stati registrati da questo snap-in.

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

Per ulteriori informazioni sulla registrazione degli snap-in, vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) nella [Guida per programmatori di Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Vedere anche

[Come registrare cmdlet, provider e applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
