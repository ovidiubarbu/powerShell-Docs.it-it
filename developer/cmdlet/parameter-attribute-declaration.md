---
title: Dichiarazione di attributo parametro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735145"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="402a9-102">Dichiarazione dell'attributo Parameter</span><span class="sxs-lookup"><span data-stu-id="402a9-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="402a9-103">L'attributo Parameter identifica una proprietà pubblica della classe cmdlet come un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="402a9-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="402a9-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="402a9-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="402a9-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="402a9-105">Parameters</span></span>

<span data-ttu-id="402a9-106">`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="402a9-107">`True` indica che il parametro di cmdlet è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="402a9-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="402a9-108">Se un parametro obbligatorio non viene specificato quando viene richiamato il cmdlet, Windows PowerShell richiede all'utente un valore di parametro.</span><span class="sxs-lookup"><span data-stu-id="402a9-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="402a9-109">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="402a9-109">The default is `false`.</span></span>

<span data-ttu-id="402a9-110">`ParameterSetName` ([System. String](/dotnet/api/System.String)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="402a9-111">Specifica che il parametro impostato che questo parametro di cmdlet appartiene.</span><span class="sxs-lookup"><span data-stu-id="402a9-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="402a9-112">Se non viene specificato alcun set di parametri, il parametro appartiene a tutti i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="402a9-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="402a9-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="402a9-114">Specifica la posizione del parametro all'interno di un comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="402a9-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="402a9-115">`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="402a9-116">`True` indica che il parametro del cmdlet prende il valore da un oggetto della pipeline.</span><span class="sxs-lookup"><span data-stu-id="402a9-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="402a9-117">Specificare questa parola chiave se il cmdlet accede completo dell'oggetto, non solo una proprietà dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="402a9-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="402a9-118">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="402a9-118">The default is `false`.</span></span>

<span data-ttu-id="402a9-119">`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="402a9-120">`True` indica che il parametro del cmdlet accetta il relativo valore da una proprietà di un oggetto della pipeline con lo stesso nome o lo stesso alias come parametro.</span><span class="sxs-lookup"><span data-stu-id="402a9-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="402a9-121">Se, ad esempio, il cmdlet include un `Name` parametro e l'oggetto pipeline ha anche una `Name` proprietà, il valore della `Name` proprietà viene assegnata al `Name` parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="402a9-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="402a9-122">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="402a9-122">The default is `false`.</span></span>

<span data-ttu-id="402a9-123">`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="402a9-124">`True` indica che il parametro di cmdlet accetta tutti i restanti argomenti passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="402a9-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="402a9-125">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="402a9-125">The default is `false`.</span></span>

<span data-ttu-id="402a9-126">`HelpMessage` Parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="402a9-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="402a9-127">Specifica una breve descrizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="402a9-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="402a9-128">Windows PowerShell Visualizza questo messaggio quando viene eseguito un cmdlet e un parametro obbligatorio non è specificato.</span><span class="sxs-lookup"><span data-stu-id="402a9-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="402a9-129">`HelpMessageBaseName` Parametro denominato facoltativo. Specifica la posizione in cui si trovano gli identificatori di risorsa.</span><span class="sxs-lookup"><span data-stu-id="402a9-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="402a9-130">Questo parametro, ad esempio, possibile specificare un assembly di risorse che contiene i messaggi della Guida che desideri localizzare.</span><span class="sxs-lookup"><span data-stu-id="402a9-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="402a9-131">`HelpMessageResourceId` Parametro denominato facoltativo. Specifica l'identificatore di risorsa per un messaggio della Guida.</span><span class="sxs-lookup"><span data-stu-id="402a9-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="402a9-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="402a9-132">Remarks</span></span>

- <span data-ttu-id="402a9-133">Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="402a9-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="402a9-134">Un cmdlet può avere qualsiasi numero di parametri.</span><span class="sxs-lookup"><span data-stu-id="402a9-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="402a9-135">Tuttavia, per migliorare l'esperienza utente, limitare il numero di parametri.</span><span class="sxs-lookup"><span data-stu-id="402a9-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="402a9-136">Parametri devono essere dichiarati nella proprietà o campi non statici pubblici.</span><span class="sxs-lookup"><span data-stu-id="402a9-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="402a9-137">I parametri devono essere dichiarati nella proprietà.</span><span class="sxs-lookup"><span data-stu-id="402a9-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="402a9-138">La proprietà deve avere una funzione di accesso set pubblica e se il `ValueFromPipeline` o `ValueFromPipelineByPropertyName` (parola chiave) viene specificato, la proprietà deve avere una funzione di accesso get pubblico.</span><span class="sxs-lookup"><span data-stu-id="402a9-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="402a9-139">Quando si specificano i parametri posizionali, limitare il numero di parametri posizionali in un parametro impostato su meno di cinque.</span><span class="sxs-lookup"><span data-stu-id="402a9-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="402a9-140">E, parametri posizionali non devono essere contigue.</span><span class="sxs-lookup"><span data-stu-id="402a9-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="402a9-141">Le posizioni 5 e 100 250 funzionano come le posizioni 0, 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="402a9-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="402a9-142">Quando il `Position` parola chiave non è specificato, il parametro del cmdlet è necessario fare riferimento al nome.</span><span class="sxs-lookup"><span data-stu-id="402a9-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="402a9-143">Quando si usano set di parametri, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="402a9-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="402a9-144">Ogni set di parametri deve contenere almeno un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="402a9-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="402a9-145">Progettazione dei cmdlet buona indica che questo parametro univoco del failover sarà obbligatorio se possibile.</span><span class="sxs-lookup"><span data-stu-id="402a9-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="402a9-146">Se il cmdlet è progettato per essere eseguito senza parametri, il parametro unique non può essere obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="402a9-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="402a9-147">Nessun set di parametri deve contenere più di un parametro posizionale con la stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="402a9-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="402a9-148">Un solo parametro in un set di parametri deve dichiarare `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="402a9-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="402a9-149">Possono definire più parametri `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="402a9-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="402a9-150">Possono definire più parametri `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="402a9-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="402a9-151">Per altre informazioni sulle linee guida per i nomi dei parametri, vedere [i nomi dei parametri di Cmdlet](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="402a9-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="402a9-152">L'attributo di parametro è definito per il [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="402a9-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="402a9-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="402a9-153">See Also</span></span>

[<span data-ttu-id="402a9-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="402a9-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="402a9-155">Nomi di parametro del cmdlet</span><span class="sxs-lookup"><span data-stu-id="402a9-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="402a9-156">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="402a9-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
