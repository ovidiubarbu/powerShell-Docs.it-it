---
title: Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363190"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e5d3c-102">Elemento ExpressionBinding per CustomItem per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e5d3c-103">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e5d3c-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e5d3c-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento CustomControl per il controllo per la configurazione (Format) elemento CustomEntries per CustomControl per la configurazione ( Format) elemento CustomEntry per CustomControl per i controlli per la configurazione (Format) elemento CustomItem per CustomEntry per i controlli per l'elemento Expressionation di Configuration per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5d3c-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e5d3c-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5d3c-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e5d3c-107">Attributes and Elements</span></span>

<span data-ttu-id="e5d3c-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `ExpressionBinding`.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5d3c-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="e5d3c-109">Attributes</span></span>

<span data-ttu-id="e5d3c-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5d3c-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e5d3c-111">Child Elements</span></span>

|<span data-ttu-id="e5d3c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5d3c-112">Element</span></span>|<span data-ttu-id="e5d3c-113">Description</span><span class="sxs-lookup"><span data-stu-id="e5d3c-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e5d3c-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e5d3c-115">Definisce un controllo utilizzato dal controllo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e5d3c-116">Elemento CustomControlName per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5d3c-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e5d3c-118">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e5d3c-119">Elemento enumeratorcollection per Expressions per i controlli per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5d3c-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e5d3c-121">Specifica che gli elementi delle raccolte vengono visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="e5d3c-122">Elemento ItemSelectionCondition per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5d3c-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e5d3c-124">Definisce la condizione che deve esistere affinché questo controllo comune venga usato.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="e5d3c-125">Elemento PropertyName per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5d3c-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e5d3c-127">Specifica la proprietà .NET il cui valore viene visualizzato dal controllo comune.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="e5d3c-128">Elemento ScriptBlock per ExpressionName per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="e5d3c-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5d3c-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e5d3c-130">Specifica lo script il cui valore viene visualizzato dal controllo comune.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5d3c-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e5d3c-131">Parent Elements</span></span>

|<span data-ttu-id="e5d3c-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5d3c-132">Element</span></span>|<span data-ttu-id="e5d3c-133">Description</span><span class="sxs-lookup"><span data-stu-id="e5d3c-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5d3c-134">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="e5d3c-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e5d3c-135">Definisce quali dati vengono visualizzati dalla visualizzazione controlli personalizzati e come vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="e5d3c-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5d3c-136">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e5d3c-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e5d3c-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e5d3c-137">See Also</span></span>

[<span data-ttu-id="e5d3c-138">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="e5d3c-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5d3c-139">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5d3c-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
