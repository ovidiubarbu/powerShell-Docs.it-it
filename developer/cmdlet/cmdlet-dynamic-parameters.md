---
title: I parametri di cmdlet dinamica | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853807"
---
# <a name="cmdlet-dynamic-parameters"></a>Parametri dinamici dei cmdlet

I cmdlet possono definire i parametri disponibili per l'utente in condizioni speciali, ad esempio quando l'argomento di un altro parametro è un valore specifico. Questi parametri vengono aggiunti in fase di esecuzione e sono dette *parametri dinamici* poiché essi vengono aggiunti solo quando sono necessari. Ad esempio, è possibile progettare un cmdlet che aggiunge diversi parametri solo quando viene specificato un parametro di commutatore specifico.

> [!NOTE]
> I provider e le funzioni di Windows PowerShell possono anche definire i parametri dinamici.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Parametri dinamici nei cmdlet di Windows PowerShell

Windows PowerShell Usa i parametri dinamici in molti dei cmdlet relativi provider. Ad esempio, il `Get-Item` e `Get-ChildItem` cmdlet di aggiungere un `CodeSigningCert` parametro in fase di esecuzione quando il `Path` parametro del cmdlet specifica il percorso di provider di certificati. Se il `Path` parametri del cmdlet consente di specificare un percorso per un provider diverso, il `CodeSigningCert` parametro non è disponibile.

Gli esempi seguenti illustrano come il `CodeSigningCert` parametro viene aggiunto in fase di esecuzione quando il `Get-Item` cmdlet viene eseguito.

Nel primo esempio, il runtime di Windows PowerShell è stato aggiunto il parametro e il cmdlet ha esito positivo.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

Nel secondo esempio, viene specificata un'unità file System e viene restituito un errore. Il messaggio di errore indica che il `CodeSigningCert` parametro nebyla nalezena.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Supporto per i parametri dinamici

Per supportare i parametri dinamici, il codice del cmdlet è necessario includere gli elementi seguenti.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) questa interfaccia fornisce il metodo che recupera i parametri dinamici.

Esempio:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) questo metodo recupera l'oggetto che contiene le definizioni dei parametri dinamici.

Esempio:

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

Classe di parametri dinamici questa classe definisce i parametri da aggiungere. Questa classe deve includere un attributo di parametro per ogni parametro e qualsiasi Alias e convalida gli attributi facoltativi che sono necessari per il cmdlet.

Esempio:

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

Per un esempio completo di cmdlet che supporta i parametri dinamici, vedere [come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
