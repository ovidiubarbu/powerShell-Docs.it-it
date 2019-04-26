---
title: Dichiarazione di proprietà come parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068267"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="0ec0e-102">Dichiarazione di proprietà come parametri</span><span class="sxs-lookup"><span data-stu-id="0ec0e-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="0ec0e-103">In questo argomento fornisce informazioni di base che è necessario comprendere prima di dichiarare i parametri di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="0ec0e-104">Per dichiarare i parametri di un cmdlet all'interno della classe cmdlet, definire le proprietà pubbliche che rappresentano ogni parametro e quindi aggiungere uno o più attributi di parametro per ogni proprietà.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="0ec0e-105">Il runtime di Windows PowerShell Usa gli attributi di parametro per identificare la proprietà come parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="0ec0e-106">La sintassi di base per dichiarare l'attributo di parametro è `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="0ec0e-107">Di seguito è riportato un esempio di una proprietà definita come un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="0ec0e-108">Ecco alcuni aspetti da ricordare riguardo a parametri.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="0ec0e-109">Un parametro deve essere esplicitamente contrassegnato come pubblico.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="0ec0e-110">Parametri non contrassegnati come pubblici impostati come interni e non verranno trovati dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="0ec0e-111">I parametri devono essere definiti come tipi di Microsoft .NET Framework per fornire una migliore convalida dei parametri.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="0ec0e-112">Ad esempio, i parametri che sono limitati a un valore all'esterno di un set di valori devono essere definiti come un tipo di enumerazione.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="0ec0e-113">I parametri che accettano un valore di Uniform Resource Identifier (URI) devono essere di tipo [System. URI](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="0ec0e-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="0ec0e-114">Evitare di parametri di base su stringhe per le proprietà tutto tranne testo libero.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="0ec0e-115">È possibile aggiungere un parametro a qualsiasi numero di set di parametri.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="0ec0e-116">Per altre informazioni sui set di parametri, vedere [imposta parametro di Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0ec0e-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="0ec0e-117">Windows PowerShell fornisce anche un set di parametri comuni che sono automaticamente disponibili per ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ec0e-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="0ec0e-118">Per altre informazioni su questi parametri e i relativi alias, vedere [parametri comuni del Cmdlet](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="0ec0e-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ec0e-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ec0e-119">See Also</span></span>

[<span data-ttu-id="0ec0e-120">Parametri comuni di cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ec0e-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="0ec0e-121">Tipi di parametro del Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ec0e-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="0ec0e-122">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ec0e-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
