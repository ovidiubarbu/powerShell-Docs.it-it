---
title: La scrittura di uno Snap-in PowerShell di Windows personalizzata | Microsoft Docs
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
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863347"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Scrittura di uno snap-in di Windows PowerShell personalizzato

In questo esempio viene illustrato come scrivere uno snap-in Windows PowerShell che registra i cmdlet specifici.

Con questo tipo di snap-in, specificare quali cmdlet, provider, tipi o formati da registrare. Per altre informazioni su come scrivere uno snap-in che registra tutti i cmdlet e provider in un assembly, vedere [scrivere uno Snap-in PowerShell di Windows](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Per scrivere uno Snap-in PowerShell di Windows che effettua la registrazione cmdlet specifici.

1. Aggiungere l'attributo RunInstallerAttribute.

2. Creare una classe pubblica che deriva dal [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe.

   In questo esempio, il nome della classe è "CustomPSSnapinTest".

3. Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio). Quando si rinomina gli snap-in, non usare uno qualsiasi dei seguenti caratteri: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   In questo esempio, il nome dello snap-in è "CustomPSSnapInTest".

4. Aggiungere una proprietà pubblica del fornitore dello snap-in (obbligatorio).

   In questo esempio, il fornitore è "Microsoft".

5. Aggiungere una proprietà pubblica per la risorsa di fornitore dello snap-in (facoltativo).

   In questo esempio, la risorsa di fornitore è "CustomPSSnapInTest, Microsoft".

6. Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).

   In questo esempio, la descrizione è: "È uno personalizzato snap-in Windows PowerShell che include il Test-HelloWorld e il cmdlet Test-CustomSnapinTest."

7. Aggiungere una proprietà pubblica per la risorsa di descrizione dello snap-in (facoltativo).

   In questo esempio, la risorsa del fornitore è "CustomPSSnapInTest, questo è uno personalizzato snap-in Windows PowerShell che include il cmdlet Test-HelloWorld e Test-CustomSnapinTest".

8. Specificare i cmdlet che appartengono ai personalizzato snap-in (facoltativo) usando il [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) classe. Le informazioni aggiunte qui includono il nome di cmdlet, il relativo tipo .NET e il nome file della Guida del cmdlet (il formato del nome di file della Guida del cmdlet dovrebbe essere help.xml di nome. dll).

   Questo esempio viene aggiunto il cmdlet Test-HelloWorld e TestCustomSnapinTest.

9. Specificare i provider che appartengono a di snap-in personalizzato (facoltativo).

   In questo esempio non specifica alcun provider.

10. Specificare i tipi che appartengono a di snap-in personalizzato (facoltativo).

    In questo esempio non viene specificato alcun tipo.

11. Specificare i formati che appartengono a di snap-in personalizzato (facoltativo).

    In questo esempio non specifica qualsiasi formato.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come scrivere uno snap-in personalizzato Windows PowerShell che può essere utilizzato per registrare il Test-HelloWorld e il cmdlet Test-CustomSnapinTest. Tenere presente che in questo esempio, l'assembly completo potrebbe contenere altri cmdlet e provider che non è registrato da questo snap-in.

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

Per altre informazioni sulla registrazione di snap-in, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) nel [Guida per programmatori di Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Vedere anche

[Come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
