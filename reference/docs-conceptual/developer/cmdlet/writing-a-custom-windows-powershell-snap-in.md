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
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="290b0-102">Scrittura di uno snap-in di Windows PowerShell personalizzato</span><span class="sxs-lookup"><span data-stu-id="290b0-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="290b0-103">Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che registra cmdlet specifici.</span><span class="sxs-lookup"><span data-stu-id="290b0-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="290b0-104">Con questo tipo di snap-in è possibile specificare i cmdlet, i provider, i tipi o i formati da registrare.</span><span class="sxs-lookup"><span data-stu-id="290b0-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="290b0-105">Per ulteriori informazioni sulla scrittura di uno snap-in che registra tutti i cmdlet e i provider in un assembly, vedere [scrittura di uno snap-in di Windows PowerShell](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="290b0-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="290b0-106">Per scrivere uno snap-in di Windows PowerShell che registra cmdlet specifici.</span><span class="sxs-lookup"><span data-stu-id="290b0-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="290b0-107">Aggiungere l'attributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="290b0-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="290b0-108">Creare una classe pubblica che deriva dalla classe [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="290b0-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="290b0-109">In questo esempio, il nome della classe è "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="290b0-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="290b0-110">Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="290b0-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="290b0-111">Quando si assegnano nomi agli snap-in, non usare i caratteri seguenti: #.</span><span class="sxs-lookup"><span data-stu-id="290b0-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="290b0-112">, () {} [] &-/\ $; : "' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="290b0-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="290b0-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="290b0-113">@ \` \*</span></span>

   <span data-ttu-id="290b0-114">In questo esempio, il nome dello snap-in è "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="290b0-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="290b0-115">Aggiungere una proprietà pubblica per il fornitore dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="290b0-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="290b0-116">In questo esempio, il fornitore è "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="290b0-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="290b0-117">Aggiungere una proprietà pubblica per la risorsa fornitore dello snap-in (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="290b0-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="290b0-118">In questo esempio, la risorsa fornitore è "CustomPSSnapInTest, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="290b0-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="290b0-119">Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="290b0-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="290b0-120">In questo esempio la descrizione è: "si tratta di uno snap-in di Windows PowerShell personalizzato che include i cmdlet test-HelloWorld e test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="290b0-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="290b0-121">Aggiungere una proprietà pubblica per la risorsa Description dello snap-in (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="290b0-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="290b0-122">In questo esempio, la risorsa fornitore è "CustomPSSnapInTest", si tratta di uno snap-in di Windows PowerShell personalizzato che include i cmdlet test-HelloWorld e test-CustomSnapinTest ".</span><span class="sxs-lookup"><span data-stu-id="290b0-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="290b0-123">Specificare i cmdlet che appartengono allo snap-in personalizzato (facoltativo) utilizzando la classe [System. Management. Automation. Runspaces. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) .</span><span class="sxs-lookup"><span data-stu-id="290b0-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="290b0-124">Le informazioni aggiunte includono il nome del cmdlet, il tipo .NET e il nome del file della guida del cmdlet. il formato del nome del file della guida del cmdlet deve essere Name. dll-help. XML.</span><span class="sxs-lookup"><span data-stu-id="290b0-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="290b0-125">Questo esempio aggiunge i cmdlet test-HelloWorld e TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="290b0-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="290b0-126">Specificare i provider che appartengono allo snap-in personalizzato (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="290b0-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="290b0-127">Questo esempio non specifica alcun provider.</span><span class="sxs-lookup"><span data-stu-id="290b0-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="290b0-128">Specificare i tipi che appartengono allo snap-in personalizzato (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="290b0-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="290b0-129">In questo esempio non vengono specificati tipi.</span><span class="sxs-lookup"><span data-stu-id="290b0-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="290b0-130">Specificare i formati che appartengono allo snap-in personalizzato (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="290b0-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="290b0-131">In questo esempio non viene specificato alcun formato.</span><span class="sxs-lookup"><span data-stu-id="290b0-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="290b0-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="290b0-132">Example</span></span>

<span data-ttu-id="290b0-133">Questo esempio illustra come scrivere uno snap-in di Windows PowerShell personalizzato che può essere usato per registrare i cmdlet test-HelloWorld e test-CustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="290b0-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="290b0-134">Tenere presente che in questo esempio l'assembly completo potrebbe contenere altri cmdlet e provider che non sarebbero stati registrati da questo snap-in.</span><span class="sxs-lookup"><span data-stu-id="290b0-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="290b0-135">Per ulteriori informazioni sulla registrazione degli snap-in, vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) nella [Guida per programmatori di Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="290b0-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="290b0-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="290b0-136">See Also</span></span>

[<span data-ttu-id="290b0-137">Come registrare cmdlet, provider e applicazioni host</span><span class="sxs-lookup"><span data-stu-id="290b0-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="290b0-138">SDK della shell di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="290b0-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
