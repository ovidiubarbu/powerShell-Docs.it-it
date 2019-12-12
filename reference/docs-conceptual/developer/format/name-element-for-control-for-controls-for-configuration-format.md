---
title: Elemento Name per il controllo per i controlli per la configurazione (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362710"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="c44ae-102">Elemento Name per Control per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="c44ae-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c44ae-103">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="c44ae-103">Specifies the name of the control.</span></span> <span data-ttu-id="c44ae-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="c44ae-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c44ae-105">Elemento di configurazione (Format) controlla l'elemento dell'elemento di controllo Configuration (Format) per i controlli per la configurazione (Format) elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c44ae-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c44ae-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c44ae-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c44ae-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="c44ae-107">Attributes and Elements</span></span>

<span data-ttu-id="c44ae-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `Name`.</span><span class="sxs-lookup"><span data-stu-id="c44ae-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c44ae-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="c44ae-109">Attributes</span></span>

<span data-ttu-id="c44ae-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c44ae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c44ae-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="c44ae-111">Child Elements</span></span>

<span data-ttu-id="c44ae-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="c44ae-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c44ae-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="c44ae-113">Parent Elements</span></span>

|<span data-ttu-id="c44ae-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c44ae-114">Element</span></span>|<span data-ttu-id="c44ae-115">Description</span><span class="sxs-lookup"><span data-stu-id="c44ae-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c44ae-116">Elemento Control per Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c44ae-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="c44ae-117">Definisce un controllo comune che può essere utilizzato da tutte le visualizzazioni del file di formattazione e dal nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="c44ae-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c44ae-118">Valore testo</span><span class="sxs-lookup"><span data-stu-id="c44ae-118">Text Value</span></span>

<span data-ttu-id="c44ae-119">Specificare il nome utilizzato per fare riferimento a questo controllo.</span><span class="sxs-lookup"><span data-stu-id="c44ae-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c44ae-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c44ae-120">Remarks</span></span>

<span data-ttu-id="c44ae-121">Il nome specificato qui può essere usato negli elementi seguenti per fare riferimento a questo controllo.</span><span class="sxs-lookup"><span data-stu-id="c44ae-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="c44ae-122">Quando si crea una tabella, un elenco, una visualizzazione di controlli di tipo Wide o Custom, il controllo può essere specificato dall'elemento [GroupBy per View (Format)](./groupby-element-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="c44ae-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="c44ae-123">Quando si crea un altro controllo comune, questo controllo può essere specificato dall'elemento seguente: [elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="c44ae-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="c44ae-124">Quando si crea un controllo che può essere utilizzato da una vista, questo controllo può essere specificato dall'elemento di [espressione per CustomItem per i controlli per la visualizzazione (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) .</span><span class="sxs-lookup"><span data-stu-id="c44ae-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c44ae-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c44ae-125">See Also</span></span>

[<span data-ttu-id="c44ae-126">Elemento Control per Controls per Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c44ae-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="c44ae-127">Elemento expressiongroup per CustomItem per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c44ae-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="c44ae-128">Elemento expressiongroup per CustomItem per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="c44ae-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c44ae-129">Elemento GroupBy per View (Format)</span><span class="sxs-lookup"><span data-stu-id="c44ae-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c44ae-130">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c44ae-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
