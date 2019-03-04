---
title: Imposta parametro di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857267"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="10236-102">Set di parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="10236-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="10236-103">Windows PowerShell Usa set di parametri per consentire la scrittura di un singolo cmdlet che possono eseguire azioni diverse per diversi scenari.</span><span class="sxs-lookup"><span data-stu-id="10236-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="10236-104">Set di parametri consentono di esporre parametri diversi per l'utente e per restituire informazioni diverse in base ai parametri specificati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="10236-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="10236-105">Esempi di set di parametri</span><span class="sxs-lookup"><span data-stu-id="10236-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="10236-106">Ad esempio, il `Get-EventLog` cmdlet (fornito da Windows PowerShell) restituisce informazioni diverse a seconda del fatto che l'utente specifichi il `List` o `LogName` parametro.</span><span class="sxs-lookup"><span data-stu-id="10236-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="10236-107">Se il `List` viene specificato, il cmdlet restituisce informazioni sui file di log stessi, ma non le informazioni sugli eventi che contengono.</span><span class="sxs-lookup"><span data-stu-id="10236-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="10236-108">Se il `LogName` parametro viene specificato, il cmdlet restituisce informazioni sugli eventi in un determinato registro eventi.</span><span class="sxs-lookup"><span data-stu-id="10236-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="10236-109">Il `List` e `LogName` parametro identificano due set di parametri separato.</span><span class="sxs-lookup"><span data-stu-id="10236-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="10236-110">Parametro univoco</span><span class="sxs-lookup"><span data-stu-id="10236-110">Unique Parameter</span></span>

<span data-ttu-id="10236-111">Ogni set di parametri deve avere un parametro univoco che il runtime di Windows PowerShell è possibile usare per esporre il set di parametri appropriato.</span><span class="sxs-lookup"><span data-stu-id="10236-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="10236-112">Se possibile, il parametro univoco deve essere un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="10236-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="10236-113">Quando un parametro è obbligatorio, l'utente è obbligato a specificare il parametro e il runtime di Windows PowerShell è possibile usare tale parametro per identificare il parametro impostato per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="10236-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="10236-114">Il parametro unique non può essere obbligatorio se il cmdlet è progettato per essere eseguito senza specificare alcun parametro.</span><span class="sxs-lookup"><span data-stu-id="10236-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="10236-115">Più set di parametri</span><span class="sxs-lookup"><span data-stu-id="10236-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="10236-116">Nella figura seguente, la colonna a sinistra mostra tre set di parametri valido.</span><span class="sxs-lookup"><span data-stu-id="10236-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="10236-117">Parametro oggetto è univoco per il primo set di parametri, parametro B è univoco per il secondo set di parametri e parametro C è univoco per il terzo set di parametri.</span><span class="sxs-lookup"><span data-stu-id="10236-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="10236-118">Tuttavia, nella colonna destra, i set di parametri non è un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="10236-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="10236-120">Requisiti dei Set di parametri</span><span class="sxs-lookup"><span data-stu-id="10236-120">Parameter Set Requirements</span></span>

<span data-ttu-id="10236-121">I requisiti seguenti si applicano a tutti i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="10236-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="10236-122">Ogni set di parametri deve contenere almeno un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="10236-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="10236-123">Se possibile, impostare questo parametro di un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="10236-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="10236-124">Un set di parametri che contiene più parametri posizionali debba definire le posizioni univoche per ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="10236-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="10236-125">Nessuna due parametri posizionali specificabile nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="10236-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="10236-126">Puoi dichiarare un solo parametro in un set di `ValueFromPipeline` parola chiave con il valore `true`.</span><span class="sxs-lookup"><span data-stu-id="10236-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="10236-127">Possono definire più parametri di `ValueFromPipelineByPropertyName` parola chiave con il valore `true`.</span><span class="sxs-lookup"><span data-stu-id="10236-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="10236-128">Se non viene specificato alcun set di parametri per un parametro, il parametro appartiene a tutti i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="10236-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="10236-129">Set di parametri predefiniti</span><span class="sxs-lookup"><span data-stu-id="10236-129">Default Parameter Sets</span></span>

<span data-ttu-id="10236-130">Quando sono definiti più set di parametri, è possibile usare il `DefaultParameterSetName` (parola chiave) dell'attributo Cmdlet per specificare il set di parametri predefinito.</span><span class="sxs-lookup"><span data-stu-id="10236-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="10236-131">Windows PowerShell Usa il parametro predefinito impostato se non è possibile determinare il parametro impostato per usare basato sulle informazioni fornite dal comando.</span><span class="sxs-lookup"><span data-stu-id="10236-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="10236-132">Per altre informazioni sull'attributo Cmdlet, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="10236-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="10236-133">La dichiarazione di set di parametri</span><span class="sxs-lookup"><span data-stu-id="10236-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="10236-134">Per creare un set di parametri, è necessario specificare il `ParameterSetName` parola chiave quando si dichiara l'attributo di parametro per ogni parametro nel set di parametri.</span><span class="sxs-lookup"><span data-stu-id="10236-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="10236-135">Per i parametri appartenenti a più set di parametri, aggiungere un attributo di parametro per ogni set di parametri.</span><span class="sxs-lookup"><span data-stu-id="10236-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="10236-136">Ciò consente di definire il parametro in modo diverso per ogni set di parametri.</span><span class="sxs-lookup"><span data-stu-id="10236-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="10236-137">Ad esempio, è possibile definire un parametro come obbligatori in un set e facoltativi in un altro.</span><span class="sxs-lookup"><span data-stu-id="10236-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="10236-138">Tuttavia, ogni set di parametri deve contenere un solo parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="10236-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="10236-139">Nell'esempio seguente, il `UserName` parametro è il parametro unique di set di parametri Test01 e il `ComputerName` parametro è il parametro unique di set di parametri Test02.</span><span class="sxs-lookup"><span data-stu-id="10236-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="10236-140">Il `SharedParam` parametro appartiene a entrambi i set ed è obbligatorio per il parametro Test01 impostata ma facoltativo per il set di parametri Test02.</span><span class="sxs-lookup"><span data-stu-id="10236-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```