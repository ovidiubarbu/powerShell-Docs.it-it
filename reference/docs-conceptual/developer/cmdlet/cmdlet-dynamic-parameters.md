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
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="aa7d7-102">Parametri dinamici cmdlet</span><span class="sxs-lookup"><span data-stu-id="aa7d7-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="aa7d7-103">I cmdlet possono definire parametri disponibili per l'utente in condizioni speciali, ad esempio quando l'argomento di un altro parametro è un valore specifico.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="aa7d7-104">Questi parametri vengono aggiunti in fase di esecuzione e vengono definiti parametri dinamici perché vengono aggiunti solo quando necessario.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="aa7d7-105">È ad esempio possibile progettare un cmdlet che aggiunge diversi parametri solo quando viene specificato un parametro di opzione specifico.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="aa7d7-106">I provider e le funzioni di PowerShell possono anche definire parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="aa7d7-107">Parametri dinamici nei cmdlet di PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa7d7-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="aa7d7-108">PowerShell usa parametri dinamici in diversi cmdlet del provider.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="aa7d7-109">I cmdlet `Get-Item` e `Get-ChildItem`, ad esempio, aggiungono un parametro **CodeSigningCert** in fase di esecuzione quando il parametro **path** specifica il percorso del provider di **certificati** .</span><span class="sxs-lookup"><span data-stu-id="aa7d7-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="aa7d7-110">Se il parametro **path** specifica un percorso per un provider diverso, il parametro **CodeSigningCert** non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="aa7d7-111">Negli esempi seguenti viene illustrato il modo in cui il parametro **CodeSigningCert** viene aggiunto in fase di esecuzione quando viene eseguito `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="aa7d7-112">In questo esempio, il runtime di PowerShell ha aggiunto il parametro e il cmdlet ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="aa7d7-113">In questo esempio viene specificata un'unità **filesystem** e viene restituito un errore.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="aa7d7-114">Il messaggio di errore indica che il parametro **CodeSigningCert** non è stato trovato.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

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

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="aa7d7-115">Supporto per parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="aa7d7-115">Support for dynamic parameters</span></span>

<span data-ttu-id="aa7d7-116">Per supportare i parametri dinamici, è necessario includere nel codice del cmdlet gli elementi seguenti.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="aa7d7-117">Interfaccia</span><span class="sxs-lookup"><span data-stu-id="aa7d7-117">Interface</span></span>

<span data-ttu-id="aa7d7-118">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="aa7d7-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="aa7d7-119">Questa interfaccia fornisce il metodo che recupera i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="aa7d7-120">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="aa7d7-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="aa7d7-121">Metodo</span><span class="sxs-lookup"><span data-stu-id="aa7d7-121">Method</span></span>

<span data-ttu-id="aa7d7-122">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="aa7d7-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="aa7d7-123">Questo metodo recupera l'oggetto che contiene le definizioni dei parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="aa7d7-124">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="aa7d7-124">For example:</span></span>

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

### <a name="class"></a><span data-ttu-id="aa7d7-125">Classe</span><span class="sxs-lookup"><span data-stu-id="aa7d7-125">Class</span></span>

<span data-ttu-id="aa7d7-126">Classe che definisce i parametri dinamici da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="aa7d7-127">Questa classe deve includere un attributo di **parametro** per ogni parametro e gli eventuali attributi facoltativi di **convalida** e **alias** richiesti dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa7d7-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="aa7d7-128">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="aa7d7-128">For example:</span></span>

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

<span data-ttu-id="aa7d7-129">Per un esempio completo di un cmdlet che supporta i parametri dinamici, vedere [come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aa7d7-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa7d7-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aa7d7-130">See also</span></span>

[<span data-ttu-id="aa7d7-131">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="aa7d7-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="aa7d7-132">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="aa7d7-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="aa7d7-133">Come dichiarare i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="aa7d7-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="aa7d7-134">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa7d7-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
