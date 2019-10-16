---
title: Parametri dinamici dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369880"
---
# <a name="cmdlet-dynamic-parameters"></a>Parametri dinamici cmdlet

I cmdlet possono definire parametri disponibili per l'utente in condizioni speciali, ad esempio quando l'argomento di un altro parametro è un valore specifico. Questi parametri vengono aggiunti in fase di esecuzione e vengono definiti parametri dinamici perché vengono aggiunti solo quando necessario. È ad esempio possibile progettare un cmdlet che aggiunge diversi parametri solo quando viene specificato un parametro di opzione specifico.

> [!NOTE]
> I provider e le funzioni di PowerShell possono anche definire parametri dinamici.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Parametri dinamici nei cmdlet di PowerShell

PowerShell usa parametri dinamici in diversi cmdlet del provider. I cmdlet `Get-Item` e `Get-ChildItem`, ad esempio, aggiungono un parametro **CodeSigningCert** in fase di esecuzione quando il parametro **path** specifica il percorso del provider di **certificati** . Se il parametro **path** specifica un percorso per un provider diverso, il parametro **CodeSigningCert** non è disponibile.

Negli esempi seguenti viene illustrato il modo in cui il parametro **CodeSigningCert** viene aggiunto in fase di esecuzione quando viene eseguito `Get-Item`.

In questo esempio, il runtime di PowerShell ha aggiunto il parametro e il cmdlet ha esito positivo.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

In questo esempio viene specificata un'unità **filesystem** e viene restituito un errore. Il messaggio di errore indica che il parametro **CodeSigningCert** non è stato trovato.

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Supporto per parametri dinamici

Per supportare i parametri dinamici, è necessario includere nel codice del cmdlet gli elementi seguenti.

### <a name="interface"></a>Interfaccia

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Questa interfaccia fornisce il metodo che recupera i parametri dinamici.

Ad esempio:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Metodo

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Questo metodo recupera l'oggetto che contiene le definizioni dei parametri dinamici.

Ad esempio:

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

### <a name="class"></a>Classe

Classe che definisce i parametri dinamici da aggiungere. Questa classe deve includere un attributo di **parametro** per ogni parametro e gli eventuali attributi facoltativi di **convalida** e **alias** richiesti dal cmdlet.

Ad esempio:

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

Per un esempio completo di un cmdlet che supporta i parametri dinamici, vedere [come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
