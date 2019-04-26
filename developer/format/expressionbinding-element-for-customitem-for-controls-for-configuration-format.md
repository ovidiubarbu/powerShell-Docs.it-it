---
title: Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065944"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="c46c6-102">Elemento ExpressionBinding per CustomItem per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c46c6-103">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="c46c6-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c46c6-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c46c6-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli di configurazione (formato) CustomControl elemento per il controllo per elemento di configurazione (formato) CustomEntries per CustomControl per Configuration ( Elemento CustomEntry Format) per CustomControl per i controlli per elemento di configurazione (formato) CustomItem per CustomEntry per i controlli per configurazione ExpressionBinding elemento CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c46c6-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c46c6-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c46c6-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="c46c6-107">Attributes and Elements</span></span>

<span data-ttu-id="c46c6-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="c46c6-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c46c6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c46c6-109">Attributes</span></span>

<span data-ttu-id="c46c6-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c46c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c46c6-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c46c6-111">Child Elements</span></span>

|<span data-ttu-id="c46c6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c46c6-112">Element</span></span>|<span data-ttu-id="c46c6-113">Description</span><span class="sxs-lookup"><span data-stu-id="c46c6-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="c46c6-114">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c46c6-115">Definisce un controllo che viene utilizzato da questo controllo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="c46c6-116">Elemento CustomControlName per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="c46c6-117">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c46c6-118">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c46c6-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="c46c6-119">Elemento EnumerateCollection per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="c46c6-120">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c46c6-121">Specificare che gli elementi delle raccolte vengono visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="c46c6-122">Elemento ItemSelectionCondition per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="c46c6-123">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-123">Optional element.</span></span><br /><br /> <span data-ttu-id="c46c6-124">Definisce la condizione che deve essere presente per questo controllo comune da usare.</span><span class="sxs-lookup"><span data-stu-id="c46c6-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="c46c6-125">Elemento PropertyName per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="c46c6-126">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c46c6-127">Specifica la proprietà .NET il cui valore viene visualizzato per il controllo comune.</span><span class="sxs-lookup"><span data-stu-id="c46c6-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="c46c6-128">Elemento ScriptBlock per ExpressionBinding per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="c46c6-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="c46c6-129">Elemento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="c46c6-129">Optional element.</span></span><br /><br /> <span data-ttu-id="c46c6-130">Specifica lo script il cui valore viene visualizzato per il controllo comune.</span><span class="sxs-lookup"><span data-stu-id="c46c6-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c46c6-131">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c46c6-131">Parent Elements</span></span>

|<span data-ttu-id="c46c6-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="c46c6-132">Element</span></span>|<span data-ttu-id="c46c6-133">Description</span><span class="sxs-lookup"><span data-stu-id="c46c6-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c46c6-134">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="c46c6-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="c46c6-135">Definisce i dati visualizzati dalla visualizzazione del controllo personalizzato e modalità di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c46c6-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c46c6-136">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c46c6-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c46c6-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c46c6-137">See Also</span></span>

[<span data-ttu-id="c46c6-138">Elemento CustomItem per CustomEntry per i controlli per la configurazione</span><span class="sxs-lookup"><span data-stu-id="c46c6-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="c46c6-139">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c46c6-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
