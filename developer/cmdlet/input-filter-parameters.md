---
title: Filtro parametri di input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854467"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="857f1-102">Parametri di filtro degli input</span><span class="sxs-lookup"><span data-stu-id="857f1-102">Input Filter Parameters</span></span>

<span data-ttu-id="857f1-103">Un cmdlet è possibile definire `Filter`, `Include`, e `Exclude` parametri che filtrano l'insieme di oggetti di input che interessa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="857f1-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="857f1-104">In genere, il set di oggetti di input è specificato da un `InputObject`, `Path`, o `Name` parametro.</span><span class="sxs-lookup"><span data-stu-id="857f1-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="857f1-105">Ad esempio, un cmdlet può avere un `Path` parametro che accetta più percorsi con caratteri jolly e ogni percorso punta a un oggetto di input.</span><span class="sxs-lookup"><span data-stu-id="857f1-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="857f1-106">Usati insieme, il `Filter`, `Include`, e `Exclude` parametri ulteriormente qualificare i percorsi di cmdlet funziona su ogni volta che viene richiamato.</span><span class="sxs-lookup"><span data-stu-id="857f1-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="857f1-107">Includere ed escludere i parametri</span><span class="sxs-lookup"><span data-stu-id="857f1-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="857f1-108">Il `Include` e `Exclude` parametri identificano gli oggetti che sono inclusi o esclusi dal set di oggetti di input passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="857f1-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="857f1-109">Usare questi parametri quando il filtro può essere espresso nel linguaggio con caratteri jolly standard.</span><span class="sxs-lookup"><span data-stu-id="857f1-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="857f1-110">(Per altre informazioni sui caratteri jolly, vedere [che supportano i caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Il `Include` parametro include tutti gli oggetti i cui nomi corrispondono al filtro di inclusione.</span><span class="sxs-lookup"><span data-stu-id="857f1-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="857f1-111">Il `Exclude` parametro esclude tutti gli oggetti i cui nomi corrispondono al filtro.</span><span class="sxs-lookup"><span data-stu-id="857f1-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="857f1-112">Parametro di filtro</span><span class="sxs-lookup"><span data-stu-id="857f1-112">Filter Parameter</span></span>

<span data-ttu-id="857f1-113">Il `Filter` parametro specifica un filtro che non è espressa nel linguaggio con caratteri jolly standard.</span><span class="sxs-lookup"><span data-stu-id="857f1-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="857f1-114">Ad esempio, i filtri di Active Directory Service Interfaces (ADSI) o SQL potrebbero essere passati al cmdlet tramite relativo `Filter` parametro.</span><span class="sxs-lookup"><span data-stu-id="857f1-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="857f1-115">Nei cmdlet di Windows PowerShell, questi filtri vengono specificati dai provider di Windows PowerShell mediante il cmdlet per accedere a un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="857f1-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="857f1-116">In genere, ogni provider definisce un filtro.</span><span class="sxs-lookup"><span data-stu-id="857f1-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="857f1-117">Applicazione di filtri se non è specificato alcun Set di oggetti di Input</span><span class="sxs-lookup"><span data-stu-id="857f1-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="857f1-118">Se non viene specificato alcun set di oggetti di input, ciò significa in genere filtrare i dati di tutti gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="857f1-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="857f1-119">Per altre informazioni, vedere[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="857f1-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="857f1-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="857f1-120">See Also</span></span>

[<span data-ttu-id="857f1-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="857f1-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)