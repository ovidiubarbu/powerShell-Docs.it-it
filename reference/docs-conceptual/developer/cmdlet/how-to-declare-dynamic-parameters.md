---
title: Come dichiarare parametri dinamici | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364420"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="45d78-102">Come dichiarare i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="45d78-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="45d78-103">Questo esempio illustra come definire i parametri dinamici che vengono aggiunti al cmdlet in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="45d78-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="45d78-104">In questo esempio, il parametro `Department` viene aggiunto al cmdlet ogni volta che l'utente specifica il parametro dell'opzione `Employee`.</span><span class="sxs-lookup"><span data-stu-id="45d78-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="45d78-105">Per altre informazioni sui parametri dinamici, vedere [parametri dinamici dei cmdlet](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="45d78-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="45d78-106">Per definire i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="45d78-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="45d78-107">Nella dichiarazione di classe del cmdlet aggiungere l'interfaccia [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) come illustrato.</span><span class="sxs-lookup"><span data-stu-id="45d78-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="45d78-108">Chiamare il metodo [System. Management. Automation. Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) , che restituisce l'oggetto in cui sono definiti i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="45d78-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="45d78-109">In questo esempio, il metodo viene chiamato quando viene specificato il parametro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="45d78-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="45d78-110">Dichiarare una classe che definisce i parametri dinamici da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="45d78-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="45d78-111">È possibile utilizzare gli attributi utilizzati per dichiarare i parametri del cmdlet statici per dichiarare i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="45d78-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="45d78-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="45d78-112">Example</span></span>

<span data-ttu-id="45d78-113">In questo esempio, il parametro `Department` viene aggiunto ogni volta che l'utente specifica il parametro `Employee`.</span><span class="sxs-lookup"><span data-stu-id="45d78-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="45d78-114">Il parametro `Department` è un parametro facoltativo e l'attributo ValidateSet viene usato per specificare gli argomenti consentiti.</span><span class="sxs-lookup"><span data-stu-id="45d78-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="45d78-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45d78-115">See Also</span></span>

[<span data-ttu-id="45d78-116">System. Management. Automation. RuntimeDefinedParameterDictionary</span><span class="sxs-lookup"><span data-stu-id="45d78-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="45d78-117">System. Management. Automation. Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="45d78-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="45d78-118">Parametri dinamici cmdlet</span><span class="sxs-lookup"><span data-stu-id="45d78-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="45d78-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="45d78-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)