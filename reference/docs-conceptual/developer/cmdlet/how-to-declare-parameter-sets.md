---
title: Come dichiarare i set di parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365610"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="773d7-102">Come dichiarare i set di parametri</span><span class="sxs-lookup"><span data-stu-id="773d7-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="773d7-103">Questo esempio illustra come definire due set di parametri quando si dichiarano i parametri per un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="773d7-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="773d7-104">Ogni set di parametri dispone sia di un parametro univoco che di un parametro condiviso utilizzato da entrambi i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="773d7-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="773d7-105">Per ulteriori informazioni sui set di parametri, inclusa la modalità di specifica del set di parametri predefinito, vedere set di parametri del [cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="773d7-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="773d7-106">Quando possibile, definire il parametro univoco di un set di parametri come parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="773d7-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="773d7-107">Tuttavia, se si desidera che il cmdlet venga eseguito senza specificare parametri, il parametro Unique può essere un parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="773d7-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="773d7-108">Il parametro Unique del cmdlet `Get-Command`, ad esempio, è facoltativo.</span><span class="sxs-lookup"><span data-stu-id="773d7-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="773d7-109">Come definire due set di parametri</span><span class="sxs-lookup"><span data-stu-id="773d7-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="773d7-110">Aggiungere la parola chiave `ParameterSet` all'attributo Parameter per il parametro Unique del primo set di parametri.</span><span class="sxs-lookup"><span data-stu-id="773d7-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="773d7-111">Aggiungere la parola chiave `ParameterSet` all'attributo Parameter per il parametro Unique del secondo set di parametri.</span><span class="sxs-lookup"><span data-stu-id="773d7-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="773d7-112">Per il parametro che appartiene a entrambi i set di parametri, aggiungere un attributo di parametro per ogni set di parametri e quindi aggiungere la parola chiave `ParameterSet` a ogni set.</span><span class="sxs-lookup"><span data-stu-id="773d7-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="773d7-113">In ogni attributo di parametro è possibile specificare la modalità di definizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="773d7-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="773d7-114">Un parametro può essere facoltativo in un set e obbligatorio in un altro.</span><span class="sxs-lookup"><span data-stu-id="773d7-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="773d7-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="773d7-115">See Also</span></span>

[<span data-ttu-id="773d7-116">Set di parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="773d7-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="773d7-117">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="773d7-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
