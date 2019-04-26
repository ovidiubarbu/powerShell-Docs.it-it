---
title: Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065510"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="3f5eb-102">Elemento ItemSelectionCondition per ExpressionBinding per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3f5eb-103">Definisce la condizione che deve essere presente per questo controllo da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="3f5eb-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3f5eb-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per la configurazione (formato) Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f5eb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3f5eb-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f5eb-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="3f5eb-107">Attributes and Elements</span></span>

<span data-ttu-id="3f5eb-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f5eb-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3f5eb-109">Attributes</span></span>

<span data-ttu-id="3f5eb-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f5eb-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="3f5eb-111">Child Elements</span></span>

|<span data-ttu-id="3f5eb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f5eb-112">Element</span></span>|<span data-ttu-id="3f5eb-113">Description</span><span class="sxs-lookup"><span data-stu-id="3f5eb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f5eb-114">Elemento PropertyName per ItemSelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3f5eb-115">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3f5eb-116">Specifica la proprietà .NET che attiva la condizione.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3f5eb-117">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="3f5eb-118">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3f5eb-119">Specifica lo script che genera la condizione.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3f5eb-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="3f5eb-120">Parent Elements</span></span>

|<span data-ttu-id="3f5eb-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f5eb-121">Element</span></span>|<span data-ttu-id="3f5eb-122">Description</span><span class="sxs-lookup"><span data-stu-id="3f5eb-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f5eb-123">Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3f5eb-124">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f5eb-125">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3f5eb-125">Remarks</span></span>

<span data-ttu-id="3f5eb-126">È possibile specificare un nome di proprietà o uno script per questa condizione, ma non è possibile specificare entrambi.</span><span class="sxs-lookup"><span data-stu-id="3f5eb-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f5eb-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f5eb-127">See Also</span></span>

[<span data-ttu-id="3f5eb-128">Elemento PropertyName per ItemSelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3f5eb-129">Elemento ScriptBlock per ItemSelectionCondition per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="3f5eb-130">Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="3f5eb-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3f5eb-131">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f5eb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
