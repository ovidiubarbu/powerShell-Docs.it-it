---
title: Parametri del filtro di input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364390"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="0327f-102">Parametri di filtro degli input</span><span class="sxs-lookup"><span data-stu-id="0327f-102">Input Filter Parameters</span></span>

<span data-ttu-id="0327f-103">Un cmdlet può definire i parametri `Filter`, `Include` e `Exclude` che filtrano il set di oggetti di input interessati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0327f-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="0327f-104">In genere, il set di oggetti di input viene specificato da un parametro `InputObject`, `Path` o `Name`.</span><span class="sxs-lookup"><span data-stu-id="0327f-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="0327f-105">Ad esempio, un cmdlet può avere un parametro `Path` che accetta più percorsi utilizzando caratteri jolly e ogni percorso punta a un oggetto di input.</span><span class="sxs-lookup"><span data-stu-id="0327f-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="0327f-106">Insieme, i parametri `Filter`, `Include` e `Exclude` qualificano ulteriormente i percorsi utilizzati dal cmdlet ogni volta che viene richiamato.</span><span class="sxs-lookup"><span data-stu-id="0327f-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="0327f-107">Includi ed Escludi parametri</span><span class="sxs-lookup"><span data-stu-id="0327f-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="0327f-108">I parametri `Include` e `Exclude` identificano gli oggetti inclusi o esclusi dal set di oggetti di input passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0327f-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="0327f-109">Usare questi parametri quando il filtro può essere espresso nel linguaggio con caratteri jolly standard.</span><span class="sxs-lookup"><span data-stu-id="0327f-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="0327f-110">Per ulteriori informazioni sui caratteri jolly, vedere Supporto dei caratteri [jolly nei parametri dei cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md). Il parametro `Include` include tutti gli oggetti i cui nomi corrispondono al filtro di inclusione.</span><span class="sxs-lookup"><span data-stu-id="0327f-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="0327f-111">Il parametro `Exclude` esclude tutti gli oggetti i cui nomi corrispondono al filtro.</span><span class="sxs-lookup"><span data-stu-id="0327f-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="0327f-112">Parametro Filter</span><span class="sxs-lookup"><span data-stu-id="0327f-112">Filter Parameter</span></span>

<span data-ttu-id="0327f-113">Il parametro `Filter` specifica un filtro non espresso nel linguaggio con caratteri jolly standard.</span><span class="sxs-lookup"><span data-stu-id="0327f-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="0327f-114">È ad esempio possibile passare al cmdlet i filtri ADSI (Active Directory Service Interfaces) o SQL tramite il relativo parametro `Filter`.</span><span class="sxs-lookup"><span data-stu-id="0327f-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="0327f-115">Nei cmdlet forniti da Windows PowerShell questi filtri sono specificati dai provider di Windows PowerShell che usano il cmdlet per accedere a un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="0327f-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="0327f-116">Ogni provider definisce in genere il proprio filtro.</span><span class="sxs-lookup"><span data-stu-id="0327f-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="0327f-117">Filtro se non è specificato alcun set di oggetti di input</span><span class="sxs-lookup"><span data-stu-id="0327f-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="0327f-118">Se non viene specificato alcun set di oggetti di input, questo significa in genere filtrare in base a tutti gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="0327f-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="0327f-119">Per ulteriori informazioni, vedere[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="0327f-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="0327f-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0327f-120">See Also</span></span>

[<span data-ttu-id="0327f-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0327f-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)