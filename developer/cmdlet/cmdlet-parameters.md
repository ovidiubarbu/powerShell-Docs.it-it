---
title: Parametri del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068403"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="0b80d-102">Parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b80d-102">Cmdlet Parameters</span></span>

<span data-ttu-id="0b80d-103">Parametri del cmdlet forniscono il meccanismo che consente a un cmdlet accettare l'input.</span><span class="sxs-lookup"><span data-stu-id="0b80d-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="0b80d-104">I parametri possono accettare l'input direttamente dalla riga di comando o da oggetti passati al cmdlet tramite la pipeline, gli argomenti (noto anche come *valori*) di questi parametri possono specificare l'input che il cmdlet accetta, come il cmdlet deve eseguire le azioni e i dati restituiti dal cmdlet per la pipeline.</span><span class="sxs-lookup"><span data-stu-id="0b80d-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0b80d-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="0b80d-105">In This Section</span></span>

<span data-ttu-id="0b80d-106">[Dichiarazione di proprietà come parametri](./declaring-properties-as-parameters.md) fornisce informazioni di base è necessario comprendere prima di dichiarare i parametri di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b80d-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="0b80d-107">[Tipi di parametri del Cmdlet](./types-of-cmdlet-parameters.md) descrive i diversi tipi di parametri che è possibile dichiarare nei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b80d-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="0b80d-108">[Nome del parametro di cmdlet e linee guida per la funzionalità](./standard-cmdlet-parameter-names-and-types.md) dischi i nomi, tipo di dati e funzionalità dei parametri standard consigliati.</span><span class="sxs-lookup"><span data-stu-id="0b80d-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="0b80d-109">[Gli alias dei parametri](./parameter-aliases.md) illustra gli alias che è possibile definire per i parametri.</span><span class="sxs-lookup"><span data-stu-id="0b80d-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="0b80d-110">[I nomi dei parametri comuni](./common-parameter-names.md) in questo argomento vengono descritti i parametri che Windows PowerShell aggiunge al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b80d-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="0b80d-111">[Imposta parametro di cmdlet](./cmdlet-parameter-sets.md) viene illustrato come set di parametri consentono di scrivere un singolo cmdlet che possono eseguire azioni diverse per diversi scenari.</span><span class="sxs-lookup"><span data-stu-id="0b80d-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="0b80d-112">[I parametri dinamici cmdlet](./cmdlet-dynamic-parameters.md) vengono illustrati parametri disponibili per l'utente in condizioni speciali.</span><span class="sxs-lookup"><span data-stu-id="0b80d-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="0b80d-113">[Supporto di caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) viene descritto come fornire supporto per i caratteri jolly quando si progetta un cmdlet che verrà eseguito con un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="0b80d-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="0b80d-114">[Convalida Input parametro](./validating-parameter-input.md) illustra come la convalida di argomenti passati ai parametri del cmdlet Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b80d-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="0b80d-115">[Filtro parametri di input](./input-filter-parameters.md) esamina i `Filter`, `Include`, e `Exclude` parametri che filtrano l'insieme di oggetti di input che interessa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b80d-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0b80d-116">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="0b80d-116">Related Sections</span></span>

[<span data-ttu-id="0b80d-117">Come convalidare l'Input del parametro</span><span class="sxs-lookup"><span data-stu-id="0b80d-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="0b80d-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0b80d-118">See Also</span></span>

[<span data-ttu-id="0b80d-119">Dichiarazione di attributo di parametro</span><span class="sxs-lookup"><span data-stu-id="0b80d-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="0b80d-120">Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b80d-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
