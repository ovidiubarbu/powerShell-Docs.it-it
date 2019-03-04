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
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="21e98-102">Parametri dinamici dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="21e98-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="21e98-103">I cmdlet possono definire i parametri disponibili per l'utente in condizioni speciali, ad esempio quando l'argomento di un altro parametro è un valore specifico.</span><span class="sxs-lookup"><span data-stu-id="21e98-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="21e98-104">Questi parametri vengono aggiunti in fase di esecuzione e sono dette *parametri dinamici* poiché essi vengono aggiunti solo quando sono necessari.</span><span class="sxs-lookup"><span data-stu-id="21e98-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="21e98-105">Ad esempio, è possibile progettare un cmdlet che aggiunge diversi parametri solo quando viene specificato un parametro di commutatore specifico.</span><span class="sxs-lookup"><span data-stu-id="21e98-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="21e98-106">I provider e le funzioni di Windows PowerShell possono anche definire i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="21e98-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="21e98-107">Parametri dinamici nei cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e98-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="21e98-108">Windows PowerShell Usa i parametri dinamici in molti dei cmdlet relativi provider.</span><span class="sxs-lookup"><span data-stu-id="21e98-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="21e98-109">Ad esempio, il `Get-Item` e `Get-ChildItem` cmdlet di aggiungere un `CodeSigningCert` parametro in fase di esecuzione quando il `Path` parametro del cmdlet specifica il percorso di provider di certificati.</span><span class="sxs-lookup"><span data-stu-id="21e98-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="21e98-110">Se il `Path` parametri del cmdlet consente di specificare un percorso per un provider diverso, il `CodeSigningCert` parametro non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="21e98-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="21e98-111">Gli esempi seguenti illustrano come il `CodeSigningCert` parametro viene aggiunto in fase di esecuzione quando il `Get-Item` cmdlet viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="21e98-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="21e98-112">Nel primo esempio, il runtime di Windows PowerShell è stato aggiunto il parametro e il cmdlet ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="21e98-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="21e98-113">Nel secondo esempio, viene specificata un'unità file System e viene restituito un errore.</span><span class="sxs-lookup"><span data-stu-id="21e98-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="21e98-114">Il messaggio di errore indica che il `CodeSigningCert` parametro nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="21e98-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

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

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="21e98-115">Supporto per i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="21e98-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="21e98-116">Per supportare i parametri dinamici, il codice del cmdlet è necessario includere gli elementi seguenti.</span><span class="sxs-lookup"><span data-stu-id="21e98-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="21e98-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) questa interfaccia fornisce il metodo che recupera i parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="21e98-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="21e98-118">Esempio:</span><span class="sxs-lookup"><span data-stu-id="21e98-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="21e98-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) questo metodo recupera l'oggetto che contiene le definizioni dei parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="21e98-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="21e98-120">Esempio:</span><span class="sxs-lookup"><span data-stu-id="21e98-120">Example:</span></span>

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

<span data-ttu-id="21e98-121">Classe di parametri dinamici questa classe definisce i parametri da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="21e98-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="21e98-122">Questa classe deve includere un attributo di parametro per ogni parametro e qualsiasi Alias e convalida gli attributi facoltativi che sono necessari per il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21e98-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="21e98-123">Esempio:</span><span class="sxs-lookup"><span data-stu-id="21e98-123">Example:</span></span>

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

<span data-ttu-id="21e98-124">Per un esempio completo di cmdlet che supporta i parametri dinamici, vedere [come dichiarare i parametri dinamici](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="21e98-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21e98-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="21e98-125">See Also</span></span>

[<span data-ttu-id="21e98-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="21e98-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="21e98-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="21e98-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="21e98-128">Come dichiarare i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="21e98-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="21e98-129">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="21e98-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
