---
title: Dichiarazione dell'attributo Parameter | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365360"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="7536e-102">Dichiarazione dell'attributo Parameter</span><span class="sxs-lookup"><span data-stu-id="7536e-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="7536e-103">L'attributo Parameter identifica una proprietà pubblica della classe cmdlet come parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7536e-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="7536e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7536e-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="7536e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="7536e-105">Parameters</span></span>

<span data-ttu-id="7536e-106">`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7536e-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="7536e-107">`True` indica che il parametro del cmdlet è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7536e-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="7536e-108">Se non viene fornito un parametro obbligatorio quando viene richiamato il cmdlet, Windows PowerShell richiede all'utente un valore di parametro.</span><span class="sxs-lookup"><span data-stu-id="7536e-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="7536e-109">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="7536e-109">The default is `false`.</span></span>

<span data-ttu-id="7536e-110">`ParameterSetName` ([System. String](/dotnet/api/System.String)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7536e-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="7536e-111">Specifica il set di parametri a cui appartiene il parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7536e-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="7536e-112">Se non viene specificato alcun set di parametri, il parametro appartiene a tutti i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="7536e-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="7536e-113">`Position` ([System. Int32](/dotnet/api/System.Int32)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7536e-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="7536e-114">Specifica la posizione del parametro all'interno di un comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7536e-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="7536e-115">`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7536e-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="7536e-116">`True` indica che il parametro del cmdlet prende il valore da un oggetto pipeline.</span><span class="sxs-lookup"><span data-stu-id="7536e-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="7536e-117">Specificare questa parola chiave se il cmdlet accede all'oggetto completo, non solo a una proprietà dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="7536e-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="7536e-118">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="7536e-118">The default is `false`.</span></span>

<span data-ttu-id="7536e-119">`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7536e-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="7536e-120">`True` indica che il parametro del cmdlet prende il valore da una proprietà di un oggetto pipeline con lo stesso nome o lo stesso alias di questo parametro.</span><span class="sxs-lookup"><span data-stu-id="7536e-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="7536e-121">Se, ad esempio, il cmdlet dispone di un parametro `Name` e l'oggetto pipeline dispone anche di una proprietà `Name`, il valore della proprietà `Name` viene assegnato al parametro `Name` del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7536e-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="7536e-122">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="7536e-122">The default is `false`.</span></span>

<span data-ttu-id="7536e-123">`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7536e-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="7536e-124">`True` indica che il parametro del cmdlet accetta tutti gli argomenti rimanenti passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7536e-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="7536e-125">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="7536e-125">The default is `false`.</span></span>

<span data-ttu-id="7536e-126">parametro denominato facoltativo `HelpMessage`.</span><span class="sxs-lookup"><span data-stu-id="7536e-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="7536e-127">Specifica una breve descrizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="7536e-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="7536e-128">Windows PowerShell Visualizza questo messaggio quando viene eseguito un cmdlet e non viene specificato un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7536e-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="7536e-129">parametro denominato facoltativo `HelpMessageBaseName`. Specifica la posizione in cui risiedono gli identificatori di risorsa.</span><span class="sxs-lookup"><span data-stu-id="7536e-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="7536e-130">Questo parametro, ad esempio, può specificare un assembly di risorse che contiene i messaggi della guida che si desidera localizzare.</span><span class="sxs-lookup"><span data-stu-id="7536e-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="7536e-131">parametro denominato facoltativo `HelpMessageResourceId`. Specifica l'identificatore di risorsa per un messaggio della guida.</span><span class="sxs-lookup"><span data-stu-id="7536e-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="7536e-132">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7536e-132">Remarks</span></span>

- <span data-ttu-id="7536e-133">Per ulteriori informazioni su come dichiarare questo attributo, vedere [come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7536e-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="7536e-134">Un cmdlet può avere un numero qualsiasi di parametri.</span><span class="sxs-lookup"><span data-stu-id="7536e-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="7536e-135">Tuttavia, per un'esperienza utente migliore, limitare il numero di parametri.</span><span class="sxs-lookup"><span data-stu-id="7536e-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="7536e-136">I parametri devono essere dichiarati in proprietà o campi non statici pubblici.</span><span class="sxs-lookup"><span data-stu-id="7536e-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="7536e-137">I parametri devono essere dichiarati in proprietà.</span><span class="sxs-lookup"><span data-stu-id="7536e-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="7536e-138">La proprietà deve disporre di una funzione di accesso set pubblica. Se si specifica la parola chiave `ValueFromPipeline` o `ValueFromPipelineByPropertyName`, la proprietà deve disporre di una funzione di accesso get pubblica.</span><span class="sxs-lookup"><span data-stu-id="7536e-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="7536e-139">Quando si specificano parametri posizionali, limitare il numero di parametri posizionali in un parametro impostato su un valore minore di 5.</span><span class="sxs-lookup"><span data-stu-id="7536e-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="7536e-140">E, i parametri posizionali non devono essere contigui.</span><span class="sxs-lookup"><span data-stu-id="7536e-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="7536e-141">Le posizioni 5, 100 e 250 funzionano allo stesso modo delle posizioni 0, 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="7536e-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="7536e-142">Quando non viene specificata la parola chiave `Position`, il relativo nome deve essere usato come riferimento al parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7536e-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="7536e-143">Quando si usano i set di parametri, tenere presente quanto segue:</span><span class="sxs-lookup"><span data-stu-id="7536e-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="7536e-144">Ogni set di parametri deve avere almeno un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="7536e-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="7536e-145">Una progettazione di cmdlet efficace indica che questo parametro univoco deve essere obbligatorio, se possibile.</span><span class="sxs-lookup"><span data-stu-id="7536e-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="7536e-146">Se il cmdlet è progettato per l'esecuzione senza parametri, il parametro Unique non può essere obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="7536e-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="7536e-147">Nessun set di parametri deve contenere più di un parametro posizionale con la stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="7536e-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="7536e-148">Solo un parametro in un set di parametri deve dichiarare `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="7536e-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="7536e-149">Più parametri possono definire `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="7536e-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="7536e-150">Più parametri possono definire `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="7536e-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="7536e-151">Per ulteriori informazioni sulle linee guida per i nomi dei parametri, vedere [cmdlet parameter names](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="7536e-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="7536e-152">L'attributo Parameter è definito dalla classe [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="7536e-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7536e-153">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7536e-153">See Also</span></span>

[<span data-ttu-id="7536e-154">System. Management. Automation. ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="7536e-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="7536e-155">Nomi dei parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="7536e-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="7536e-156">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7536e-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
