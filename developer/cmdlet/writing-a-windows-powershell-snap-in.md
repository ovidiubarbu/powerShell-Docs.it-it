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
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322947"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="25cd6-102">Scrittura di uno snap-in di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25cd6-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="25cd6-103">Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che può essere usato per registrare tutti i cmdlet e i provider di Windows PowerShell in un assembly.</span><span class="sxs-lookup"><span data-stu-id="25cd6-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="25cd6-104">Con questo tipo di snap-in non è possibile selezionare i cmdlet e i provider che si desidera registrare.</span><span class="sxs-lookup"><span data-stu-id="25cd6-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="25cd6-105">Per scrivere uno snap-in che consente di selezionare quello registrato, vedere scrittura di [uno snap-in di Windows PowerShell personalizzato](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="25cd6-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="25cd6-106">Scrittura di uno snap-in di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25cd6-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="25cd6-107">Aggiungere l'attributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="25cd6-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="25cd6-108">Creare una classe pubblica che deriva dalla classe [System. Management. Automation. pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="25cd6-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="25cd6-109">In questo esempio, il nome della classe è "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="25cd6-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="25cd6-110">Aggiungere una proprietà pubblica per il nome dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="25cd6-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="25cd6-111">Quando si assegnano nomi agli snap-in, non usare i caratteri seguenti: #.</span><span class="sxs-lookup"><span data-stu-id="25cd6-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="25cd6-112">, () {} [] &-/\ $; : "' \< >;?</span><span class="sxs-lookup"><span data-stu-id="25cd6-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="25cd6-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="25cd6-113">@ \` \*</span></span>

    <span data-ttu-id="25cd6-114">In questo esempio, il nome dello snap-in è "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="25cd6-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="25cd6-115">Aggiungere una proprietà pubblica per il fornitore dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="25cd6-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="25cd6-116">In questo esempio, il fornitore è "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="25cd6-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="25cd6-117">Aggiungere una proprietà pubblica per la risorsa fornitore dello snap-in (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="25cd6-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="25cd6-118">In questo esempio, la risorsa fornitore è "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="25cd6-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="25cd6-119">Aggiungere una proprietà pubblica per la descrizione dello snap-in (obbligatorio).</span><span class="sxs-lookup"><span data-stu-id="25cd6-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="25cd6-120">In questo esempio, la descrizione è "questo è uno snap-in di Windows PowerShell che registra il cmdlet Get-proc".</span><span class="sxs-lookup"><span data-stu-id="25cd6-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="25cd6-121">Aggiungere una proprietà pubblica per la risorsa Description dello snap-in (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="25cd6-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="25cd6-122">In questo esempio, la risorsa fornitore è "GetProcPSSnapIn01, questo è uno snap-in di Windows PowerShell che registra il cmdlet Get-proc".</span><span class="sxs-lookup"><span data-stu-id="25cd6-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="25cd6-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="25cd6-123">Example</span></span>

<span data-ttu-id="25cd6-124">Questo esempio illustra come scrivere uno snap-in di Windows PowerShell che può essere usato per registrare il cmdlet Get-proc nella shell di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25cd6-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="25cd6-125">Tenere presente che in questo esempio l'assembly completo conterrà solo la classe di snap-in GetProcPSSnapIn01 e la classe del cmdlet Get-proc.</span><span class="sxs-lookup"><span data-stu-id="25cd6-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="25cd6-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25cd6-126">See Also</span></span>

[<span data-ttu-id="25cd6-127">Come registrare cmdlet, provider e applicazioni host</span><span class="sxs-lookup"><span data-stu-id="25cd6-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="25cd6-128">SDK della shell di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25cd6-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
