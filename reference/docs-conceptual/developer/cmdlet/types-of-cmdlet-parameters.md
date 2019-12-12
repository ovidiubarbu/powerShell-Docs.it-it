---
title: Tipi di parametri dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369310"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="5038d-102">Tipi di parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="5038d-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="5038d-103">In questo argomento vengono descritti i diversi tipi di parametri che è possibile dichiarare nei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5038d-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="5038d-104">I parametri dei cmdlet possono essere posizionali, denominati, obbligatori, facoltativi o parametri di opzione.</span><span class="sxs-lookup"><span data-stu-id="5038d-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="5038d-105">Parametri posizionali e denominati</span><span class="sxs-lookup"><span data-stu-id="5038d-105">Positional and Named Parameters</span></span>

<span data-ttu-id="5038d-106">Tutti i parametri del cmdlet sono denominati o parametri posizionali.</span><span class="sxs-lookup"><span data-stu-id="5038d-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="5038d-107">Un parametro denominato richiede che si digitano il nome del parametro e l'argomento quando si chiama il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5038d-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="5038d-108">Un parametro posizionale richiede solo che si digitano gli argomenti in ordine relativo.</span><span class="sxs-lookup"><span data-stu-id="5038d-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="5038d-109">Il sistema esegue quindi il mapping del primo argomento senza nome al primo parametro posizionale.</span><span class="sxs-lookup"><span data-stu-id="5038d-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="5038d-110">Il sistema esegue il mapping tra il secondo argomento senza nome e il secondo parametro senza nome e così via.</span><span class="sxs-lookup"><span data-stu-id="5038d-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="5038d-111">Per impostazione predefinita, tutti i parametri del cmdlet sono parametri denominati.</span><span class="sxs-lookup"><span data-stu-id="5038d-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="5038d-112">Per definire un parametro denominato, omettere la parola chiave `Position` nella dichiarazione dell'attributo del **parametro** , come illustrato nella dichiarazione di parametro seguente.</span><span class="sxs-lookup"><span data-stu-id="5038d-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="5038d-113">Per definire un parametro posizionale, aggiungere la parola chiave `Position` nella dichiarazione dell'attributo Parameter, quindi specificare una posizione.</span><span class="sxs-lookup"><span data-stu-id="5038d-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="5038d-114">Nell'esempio seguente il parametro `UserName` viene dichiarato come parametro posizionale con la posizione 0.</span><span class="sxs-lookup"><span data-stu-id="5038d-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="5038d-115">Ciò significa che il primo argomento della chiamata verrà associato automaticamente a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="5038d-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="5038d-116">Una buona progettazione dei cmdlet consiglia di dichiarare i parametri più usati come parametri posizionali, in modo che l'utente non debba immettere il nome del parametro quando viene eseguito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5038d-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="5038d-117">I parametri posizionali e denominati accettano argomenti singoli o più argomenti separati da virgole.</span><span class="sxs-lookup"><span data-stu-id="5038d-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="5038d-118">Sono consentiti più argomenti solo se il parametro accetta una raccolta, ad esempio una matrice di stringhe.</span><span class="sxs-lookup"><span data-stu-id="5038d-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="5038d-119">È possibile combinare parametri posizionali e denominati nello stesso cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5038d-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="5038d-120">In questo caso, il sistema recupera prima gli argomenti denominati, quindi tenta di eseguire il mapping degli argomenti senza nome rimanenti ai parametri posizionali.</span><span class="sxs-lookup"><span data-stu-id="5038d-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="5038d-121">I comandi seguenti illustrano i diversi modi in cui è possibile specificare argomenti singoli e multipli per i parametri del cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="5038d-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="5038d-122">Si noti che negli ultimi due esempi non è necessario specificare **-Name** perché il parametro `Name` è definito come parametro posizionale.</span><span class="sxs-lookup"><span data-stu-id="5038d-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="5038d-123">Parametri obbligatori e facoltativi</span><span class="sxs-lookup"><span data-stu-id="5038d-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="5038d-124">È anche possibile definire i parametri dei cmdlet come parametri obbligatori o facoltativi.</span><span class="sxs-lookup"><span data-stu-id="5038d-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="5038d-125">È necessario specificare un parametro obbligatorio prima che il runtime di Windows PowerShell richiami il cmdlet.  Per impostazione predefinita, i parametri sono definiti come facoltativi.</span><span class="sxs-lookup"><span data-stu-id="5038d-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="5038d-126">Per definire un parametro obbligatorio, aggiungere la parola chiave `Mandatory` nella dichiarazione dell'attributo Parameter e impostarla su `true`, come illustrato nella dichiarazione di parametro seguente.</span><span class="sxs-lookup"><span data-stu-id="5038d-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="5038d-127">Per definire un parametro facoltativo, omettere la parola chiave `Mandatory` nella dichiarazione dell'attributo del **parametro** , come illustrato nella dichiarazione di parametro seguente.</span><span class="sxs-lookup"><span data-stu-id="5038d-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="5038d-128">Parametri di opzione</span><span class="sxs-lookup"><span data-stu-id="5038d-128">Switch Parameters</span></span>

<span data-ttu-id="5038d-129">Windows PowerShell fornisce un tipo [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) che consente di definire un parametro il cui valore viene impostato automaticamente su `false` se il parametro non viene specificato quando viene chiamato il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5038d-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="5038d-130">Quando possibile, usare parametri switch al posto di parametri booleani.</span><span class="sxs-lookup"><span data-stu-id="5038d-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="5038d-131">Si consideri l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="5038d-131">Consider the following sample.</span></span> <span data-ttu-id="5038d-132">Per impostazione predefinita, diversi cmdlet di Windows PowerShell non passano un oggetto di output alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5038d-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="5038d-133">Tuttavia, questi cmdlet hanno un `PassThru` parametro switch che sostituisce il comportamento predefinito.</span><span class="sxs-lookup"><span data-stu-id="5038d-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="5038d-134">Se il parametro `PassThru` viene specificato al momento della chiamata di questi cmdlet, il cmdlet restituisce un oggetto di output alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5038d-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="5038d-135">Se è necessario che il parametro abbia un valore predefinito di `true` quando il parametro non è specificato nella chiamata, provare a invertire il senso del parametro.</span><span class="sxs-lookup"><span data-stu-id="5038d-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="5038d-136">Per esempio, anziché impostare l'attributo del parametro su un valore booleano di `true`, dichiarare la proprietà come tipo [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) , quindi impostare il valore predefinito del parametro su `false`.</span><span class="sxs-lookup"><span data-stu-id="5038d-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="5038d-137">Per definire un parametro switch, dichiarare la proprietà come tipo [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="5038d-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="5038d-138">Per fare in modo che il cmdlet agisca sul parametro quando viene specificato, utilizzare la struttura seguente in uno dei metodi di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="5038d-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="5038d-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5038d-139">See Also</span></span>

[<span data-ttu-id="5038d-140">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5038d-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
