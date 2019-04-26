---
title: Tipi di parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067196"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="001eb-102">Tipi di parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="001eb-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="001eb-103">Questo argomento descrive i diversi tipi di parametri che è possibile dichiarare nei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="001eb-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="001eb-104">Parametri del cmdlet possono essere posizionali, denominati, obbligatorio, facoltativo o parametri opzionali.</span><span class="sxs-lookup"><span data-stu-id="001eb-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="001eb-105">Parametri posizionali e denominati</span><span class="sxs-lookup"><span data-stu-id="001eb-105">Positional and Named Parameters</span></span>

<span data-ttu-id="001eb-106">Tutti i parametri del cmdlet sono parametri posizionali o denominati.</span><span class="sxs-lookup"><span data-stu-id="001eb-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="001eb-107">Un parametro denominato richiede che si digita il nome del parametro e l'argomento quando si chiama il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="001eb-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="001eb-108">Un parametro posizionale richiede solo che si digitano gli argomenti nell'ordine relativo.</span><span class="sxs-lookup"><span data-stu-id="001eb-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="001eb-109">Il sistema esegue il mapping quindi il primo argomento senza nome per il primo parametro posizionale.</span><span class="sxs-lookup"><span data-stu-id="001eb-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="001eb-110">Il sistema esegue il mapping il secondo argomento senza nome per il secondo parametro senza nome e così via.</span><span class="sxs-lookup"><span data-stu-id="001eb-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="001eb-111">Per impostazione predefinita, tutti i parametri del cmdlet sono parametri denominati.</span><span class="sxs-lookup"><span data-stu-id="001eb-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="001eb-112">Per definire un parametro denominato, omettere il `Position` parola chiave nel **parametro** attributo di dichiarazione, come illustrato nella seguente dichiarazione di parametro.</span><span class="sxs-lookup"><span data-stu-id="001eb-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="001eb-113">Per definire un parametro posizionale, aggiungere il `Position` dichiarazione dell'attributo, parola chiave nel parametro e quindi specificare una posizione.</span><span class="sxs-lookup"><span data-stu-id="001eb-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="001eb-114">Nell'esempio seguente il `UserName` parametro viene dichiarato come un parametro posizionale con posizione 0.</span><span class="sxs-lookup"><span data-stu-id="001eb-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="001eb-115">Ciò significa che il primo argomento della chiamata verrà associato automaticamente a questo parametro.</span><span class="sxs-lookup"><span data-stu-id="001eb-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="001eb-116">Progettazione dei cmdlet buona consiglia che i parametri utilizzati più di essere dichiarati come parametri posizionali in modo che l'utente non dovrà immettere il nome del parametro quando si esegue il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="001eb-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="001eb-117">Parametri posizionali e denominati accettano argomenti singoli o più argomenti separati da virgole.</span><span class="sxs-lookup"><span data-stu-id="001eb-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="001eb-118">Solo se il parametro accetta una raccolta, ad esempio una matrice di stringhe, sono consentiti più argomenti.</span><span class="sxs-lookup"><span data-stu-id="001eb-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="001eb-119">È possibile combinare parametri posizionali e denominati nel cmdlet stesso.</span><span class="sxs-lookup"><span data-stu-id="001eb-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="001eb-120">In questo caso, il sistema deve recuperare prima di tutto gli argomenti denominati e quindi tenta di eseguire il mapping le rimanenti senza nome argomenti ai parametri posizionali.</span><span class="sxs-lookup"><span data-stu-id="001eb-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="001eb-121">I comandi seguenti mostrano i diversi modi in cui è possibile specificare singolo e più argomenti per i parametri del `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="001eb-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="001eb-122">Si noti che negli ultimi due esempi **-name** non dovrà essere specificato perché il `Name` parametro viene definito come un parametro posizionale.</span><span class="sxs-lookup"><span data-stu-id="001eb-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="001eb-123">Parametri obbligatori e facoltativi</span><span class="sxs-lookup"><span data-stu-id="001eb-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="001eb-124">È anche possibile definire i parametri del cmdlet come parametri obbligatori o facoltativi.</span><span class="sxs-lookup"><span data-stu-id="001eb-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="001eb-125">(Un parametro obbligatorio deve essere specificato prima che il runtime di Windows PowerShell richiama il cmdlet.)  Per impostazione predefinita, i parametri vengono definiti come facoltativi.</span><span class="sxs-lookup"><span data-stu-id="001eb-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="001eb-126">Per definire un parametro obbligatorio, aggiungere il `Mandatory` dichiarazione dell'attributo, parola chiave nel parametro e impostarlo su `true`, come illustrato nella seguente dichiarazione di parametro.</span><span class="sxs-lookup"><span data-stu-id="001eb-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="001eb-127">Per definire un parametro facoltativo, omettere il `Mandatory` parola chiave nel **parametro** attributo di dichiarazione, come illustrato nella seguente dichiarazione di parametro.</span><span class="sxs-lookup"><span data-stu-id="001eb-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="001eb-128">Parametri opzionali</span><span class="sxs-lookup"><span data-stu-id="001eb-128">Switch Parameters</span></span>

<span data-ttu-id="001eb-129">Windows PowerShell fornisce un' [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo che consente di definire un parametro il cui valore viene impostato automaticamente su `false` se il parametro non viene specificato quando è il cmdlet viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="001eb-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="001eb-130">Se possibile, usare parametri di opzione anziché i parametri booleani.</span><span class="sxs-lookup"><span data-stu-id="001eb-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="001eb-131">Si consideri l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="001eb-131">Consider the following sample.</span></span> <span data-ttu-id="001eb-132">Per impostazione predefinita, alcuni cmdlet di Windows PowerShell non passare un oggetto di output alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="001eb-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="001eb-133">Tuttavia, questi cmdlet hanno un `PassThru` passare parametri che esegue l'override del comportamento predefinito.</span><span class="sxs-lookup"><span data-stu-id="001eb-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="001eb-134">Se il `PassThru` viene specificato quando vengono chiamati questi cmdlet, il cmdlet restituisce un oggetto di output alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="001eb-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="001eb-135">Se è necessario il parametro venga specificato un valore predefinito di `true` quando il parametro non viene specificato nella chiamata, provare a invertire il senso di parametro.</span><span class="sxs-lookup"><span data-stu-id="001eb-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="001eb-136">Per esempio, anziché impostare l'attributo di parametro da un valore booleano `true`, dichiarare la proprietà come il [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) digitare e quindi impostare il valore predefinito del parametro da `false`.</span><span class="sxs-lookup"><span data-stu-id="001eb-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="001eb-137">Per definire un parametro opzionale, dichiarare la proprietà come il [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) digitare, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="001eb-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="001eb-138">Per rendere il cmdlet agire sul parametro quando viene specificato, usare la struttura seguente all'interno di uno degli input metodi di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="001eb-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="001eb-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="001eb-139">See Also</span></span>

[<span data-ttu-id="001eb-140">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="001eb-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
