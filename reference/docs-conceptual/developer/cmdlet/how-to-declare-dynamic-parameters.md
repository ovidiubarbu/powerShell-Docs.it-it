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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364420"
---
# <a name="how-to-declare-dynamic-parameters"></a>Come dichiarare i parametri dinamici

Questo esempio illustra come definire i parametri dinamici che vengono aggiunti al cmdlet in fase di esecuzione. In questo esempio, il parametro `Department` viene aggiunto al cmdlet ogni volta che l'utente specifica il parametro dell'opzione di `Employee`. Per altre informazioni sui parametri dinamici, vedere [parametri dinamici dei cmdlet](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Per definire i parametri dinamici

1. Nella dichiarazione di classe del cmdlet aggiungere l'interfaccia [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) come illustrato.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Chiamare il metodo [System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) , che restituisce l'oggetto in cui sono definiti i parametri dinamici. In questo esempio, il metodo viene chiamato quando viene specificato il parametro `Employee`.

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

3. Dichiarare una classe che definisce i parametri dinamici da aggiungere. È possibile utilizzare gli attributi utilizzati per dichiarare i parametri del cmdlet statici per dichiarare i parametri dinamici.

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

## <a name="example"></a>Esempio

In questo esempio, il parametro `Department` viene aggiunto ogni volta che l'utente specifica il parametro `Employee`. Il parametro `Department` è un parametro facoltativo e l'attributo ValidateSet viene usato per specificare gli argomenti consentiti.

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

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Parametri dinamici cmdlet](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)