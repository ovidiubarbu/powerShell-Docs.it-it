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
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067026"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="05902-102">Scrittura di uno snap-in di Windows PowerShell personalizzato</span><span class="sxs-lookup"><span data-stu-id="05902-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="05902-103">In questo esempio viene illustrato come scrivere uno snap-in Windows PowerShell che registra i cmdlet specifici.</span><span class="sxs-lookup"><span data-stu-id="05902-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="05902-104">Con questo tipo di snap-in, specificare quali cmdlet, provider, tipi o formati da registrare.</span><span class="sxs-lookup"><span data-stu-id="05902-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="05902-105">Per altre informazioni su come scrivere uno snap-in che registra tutti i cmdlet e provider in un assembly, vedere [scrivere uno Snap-in PowerShell di Windows](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="05902-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="05902-106">Per scrivere uno Snap-in PowerShell di Windows che effettua la registrazione cmdlet specifici.</span><span class="sxs-lookup"><span data-stu-id="05902-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="05902-107">Aggiungere l'attributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="05902-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="05902-108">Creare una classe pubblica che deriva dal [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe.</span><span class="sxs-lookup"><span data-stu-id="05902-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="05902-109">In questo esempio, il nome della classe è "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="05902-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="05902-110">Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="05902-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="05902-111">Quando si rinomina gli snap-in, non usare uno qualsiasi dei seguenti caratteri: #.</span><span class="sxs-lookup"><span data-stu-id="05902-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="05902-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="05902-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="05902-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="05902-113">@ \` \*</span></span>

   <span data-ttu-id="05902-114">In questo esempio, il nome dello snap-in è "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="05902-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="05902-115">Aggiungere una proprietà pubblica del fornitore dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="05902-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="05902-116">In questo esempio, il fornitore è "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="05902-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="05902-117">Aggiungere una proprietà pubblica per la risorsa di fornitore dello snap-in (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="05902-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="05902-118">In questo esempio, la risorsa di fornitore è "CustomPSSnapInTest, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="05902-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="05902-119">Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="05902-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="05902-120">In questo esempio, la descrizione è: "È uno personalizzato snap-in Windows PowerShell che include il Test-HelloWorld e il cmdlet Test-CustomSnapinTest."</span><span class="sxs-lookup"><span data-stu-id="05902-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="05902-121">Aggiungere una proprietà pubblica per la risorsa di descrizione dello snap-in (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="05902-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="05902-122">In questo esempio, la risorsa del fornitore è "CustomPSSnapInTest, questo è uno personalizzato snap-in Windows PowerShell che include il cmdlet Test-HelloWorld e Test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="05902-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="05902-123">Specificare i cmdlet che appartengono ai personalizzato snap-in (facoltativo) usando il [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) classe.</span><span class="sxs-lookup"><span data-stu-id="05902-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="05902-124">Le informazioni aggiunte qui includono il nome di cmdlet, il relativo tipo .NET e il nome file della Guida del cmdlet (il formato del nome di file della Guida del cmdlet dovrebbe essere help.xml di nome. dll).</span><span class="sxs-lookup"><span data-stu-id="05902-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="05902-125">Questo esempio viene aggiunto il cmdlet Test-HelloWorld e TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="05902-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="05902-126">Specificare i provider che appartengono a di snap-in personalizzato (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="05902-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="05902-127">In questo esempio non specifica alcun provider.</span><span class="sxs-lookup"><span data-stu-id="05902-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="05902-128">Specificare i tipi che appartengono a di snap-in personalizzato (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="05902-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="05902-129">In questo esempio non viene specificato alcun tipo.</span><span class="sxs-lookup"><span data-stu-id="05902-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="05902-130">Specificare i formati che appartengono a di snap-in personalizzato (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="05902-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="05902-131">In questo esempio non specifica qualsiasi formato.</span><span class="sxs-lookup"><span data-stu-id="05902-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="05902-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="05902-132">Example</span></span>

<span data-ttu-id="05902-133">In questo esempio viene illustrato come scrivere uno snap-in personalizzato Windows PowerShell che può essere utilizzato per registrare il Test-HelloWorld e il cmdlet Test-CustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="05902-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="05902-134">Tenere presente che in questo esempio, l'assembly completo potrebbe contenere altri cmdlet e provider che non è registrato da questo snap-in.</span><span class="sxs-lookup"><span data-stu-id="05902-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="05902-135">Per altre informazioni sulla registrazione di snap-in, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) nel [Guida per programmatori di Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="05902-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05902-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="05902-136">See Also</span></span>

[<span data-ttu-id="05902-137">Come registrare i cmdlet, provider e applicazioni Host</span><span class="sxs-lookup"><span data-stu-id="05902-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="05902-138">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="05902-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
