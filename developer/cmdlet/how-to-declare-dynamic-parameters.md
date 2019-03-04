---
title: Come dichiarare i parametri dinamici | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857657"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="25831-102">Come dichiarare i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="25831-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="25831-103">In questo esempio viene illustrato come definire i parametri dinamici che vengono aggiunti al cmdlet in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="25831-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="25831-104">In questo esempio, il `Department` parametro viene aggiunto al cmdlet ogni volta che l'utente specifica il `Employee` parametro opzionale.</span><span class="sxs-lookup"><span data-stu-id="25831-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="25831-105">Per altre informazioni sui parametri dinamici, vedere [Cmdlet i parametri dinamici](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="25831-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="25831-106">Per definire i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="25831-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="25831-107">Nella dichiarazione di classe cmdlet, aggiungere il [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interfaccia come illustrato.</span><span class="sxs-lookup"><span data-stu-id="25831-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="25831-108">Chiamare il [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) metodo, che restituisce l'oggetto in cui vengono definiti i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="25831-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="25831-109">In questo esempio, il metodo viene chiamato quando il `Employee` parametro è specificato.</span><span class="sxs-lookup"><span data-stu-id="25831-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

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

3. <span data-ttu-id="25831-110">Dichiarare una classe che definisce i parametri dinamici da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="25831-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="25831-111">È possibile usare gli attributi che è usata per dichiarare i parametri del cmdlet statica per dichiarare i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="25831-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

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

## <a name="example"></a><span data-ttu-id="25831-112">Esempio</span><span class="sxs-lookup"><span data-stu-id="25831-112">Example</span></span>

<span data-ttu-id="25831-113">In questo esempio, il `Department` parametro viene aggiunto ogni volta che l'utente specifica il `Employee` parametro.</span><span class="sxs-lookup"><span data-stu-id="25831-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="25831-114">Il `Department` è un parametro facoltativo e l'attributo ValidateSet viene usato per specificare gli argomenti consentiti.</span><span class="sxs-lookup"><span data-stu-id="25831-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="25831-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25831-115">See Also</span></span>

[<span data-ttu-id="25831-116">System.Management.Automation.Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="25831-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="25831-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="25831-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="25831-118">Parametri di cmdlet dinamico</span><span class="sxs-lookup"><span data-stu-id="25831-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="25831-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="25831-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)