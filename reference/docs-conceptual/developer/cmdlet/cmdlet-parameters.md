---
title: Parametri dei cmdlet | Microsoft Docs
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
ms.openlocfilehash: c1d8984f4aad7bae6f9be66a2222e2c74c8afa3d
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022214"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="fbff5-102">Parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="fbff5-102">Cmdlet Parameters</span></span>

<span data-ttu-id="fbff5-103">I parametri del cmdlet forniscono il meccanismo che consente a un cmdlet di accettare l'input.</span><span class="sxs-lookup"><span data-stu-id="fbff5-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="fbff5-104">I parametri possono accettare input direttamente dalla riga di comando o da oggetti passati al cmdlet tramite la pipeline, gli argomenti (noti anche come *valori*) di questi parametri possono specificare l'input accettato dal cmdlet, il modo in cui il cmdlet deve eseguire le proprie azioni e i dati restituiti dal cmdlet alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="fbff5-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fbff5-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="fbff5-105">In This Section</span></span>

<span data-ttu-id="fbff5-106">[Dichiarazione di proprietà come parametri](./declaring-properties-as-parameters.md) Fornisce informazioni di base che è necessario conoscere prima di dichiarare i parametri di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbff5-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="fbff5-107">[Tipi di parametri dei cmdlet](./types-of-cmdlet-parameters.md) Vengono descritti i diversi tipi di parametri che è possibile dichiarare nei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbff5-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="fbff5-108">[Linee guida sul nome e la funzionalità del parametro del cmdlet](./standard-cmdlet-parameter-names-and-types.md) Vengono illustrati i nomi, il tipo di dati consigliato e la funzionalità dei parametri standard.</span><span class="sxs-lookup"><span data-stu-id="fbff5-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="fbff5-109">[Alias di parametro](./parameter-aliases.md) Vengono descritti gli alias che è possibile definire per i parametri.</span><span class="sxs-lookup"><span data-stu-id="fbff5-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="fbff5-110">[Nomi di parametro comuni](./common-parameter-names.md) In questo argomento vengono descritti i parametri aggiunti da Windows PowerShell ai cmdlet di.</span><span class="sxs-lookup"><span data-stu-id="fbff5-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="fbff5-111">[Set di parametri del cmdlet](./cmdlet-parameter-sets.md) Viene illustrato il modo in cui i set di parametri consentono di scrivere un singolo cmdlet in grado di eseguire diverse azioni per diversi scenari.</span><span class="sxs-lookup"><span data-stu-id="fbff5-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="fbff5-112">[Parametri dinamici cmdlet](./cmdlet-dynamic-parameters.md) Vengono illustrati i parametri disponibili per l'utente in condizioni particolari.</span><span class="sxs-lookup"><span data-stu-id="fbff5-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="fbff5-113">[Supporto di caratteri jolly nei parametri dei cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) Viene descritto come fornire supporto per i caratteri jolly quando si progetta un cmdlet che verrà eseguito su un gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="fbff5-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="fbff5-114">[Convalida dell'input del parametro](./validating-parameter-input.md) Descrive in che modo Windows PowerShell convalida gli argomenti passati ai parametri del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbff5-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="fbff5-115">[Parametri del filtro di input](./input-filter-parameters.md) Vengono illustrati i parametri `Filter`, `Include`e `Exclude` che filtrano il set di oggetti di input interessati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbff5-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fbff5-116">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="fbff5-116">Related Sections</span></span>

[<span data-ttu-id="fbff5-117">Come convalidare l'input del parametro</span><span class="sxs-lookup"><span data-stu-id="fbff5-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="fbff5-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fbff5-118">See Also</span></span>

[<span data-ttu-id="fbff5-119">Dichiarazione dell'attributo Parameter</span><span class="sxs-lookup"><span data-stu-id="fbff5-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="fbff5-120">Cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbff5-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
