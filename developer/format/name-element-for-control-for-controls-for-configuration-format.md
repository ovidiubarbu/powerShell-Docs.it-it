---
title: Nome elemento per il controllo per i controlli per la configurazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065190"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="029bf-102">Elemento Name per Control per Controls per Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="029bf-103">Specifica il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="029bf-103">Specifies the name of the control.</span></span> <span data-ttu-id="029bf-104">Questo elemento viene usato quando si definisce un controllo comune che può essere usato da tutte le visualizzazioni nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="029bf-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="029bf-105">Configurazione (formato) i controlli elemento di configurazione (formato) elemento di controllo per i controlli per la configurazione (formato) elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="029bf-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="029bf-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="029bf-107">Elementi e attributi</span><span class="sxs-lookup"><span data-stu-id="029bf-107">Attributes and Elements</span></span>

<span data-ttu-id="029bf-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="029bf-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="029bf-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="029bf-109">Attributes</span></span>

<span data-ttu-id="029bf-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="029bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="029bf-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="029bf-111">Child Elements</span></span>

<span data-ttu-id="029bf-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="029bf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="029bf-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="029bf-113">Parent Elements</span></span>

|<span data-ttu-id="029bf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="029bf-114">Element</span></span>|<span data-ttu-id="029bf-115">Description</span><span class="sxs-lookup"><span data-stu-id="029bf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="029bf-116">Elemento di controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="029bf-117">Definisce un controllo comune che può essere usato da tutte le visualizzazioni del file di formattazione e il nome utilizzato per fare riferimento al controllo.</span><span class="sxs-lookup"><span data-stu-id="029bf-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="029bf-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="029bf-118">Text Value</span></span>

<span data-ttu-id="029bf-119">Specificare il nome utilizzato per fare riferimento a questo controllo.</span><span class="sxs-lookup"><span data-stu-id="029bf-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="029bf-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="029bf-120">Remarks</span></span>

<span data-ttu-id="029bf-121">Il nome specificato qui è utilizzabile negli elementi seguenti per fare riferimento a questo controllo.</span><span class="sxs-lookup"><span data-stu-id="029bf-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="029bf-122">Quando si crea una tabella, elenco, visualizzazione controllo wide o personalizzato, il controllo può essere specificato dal seguente elemento: [Elemento GroupBy per visualizzazione (formato)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="029bf-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="029bf-123">Quando si crea un altro controllo comune, questo controllo può essere specificato per l'elemento seguente: [Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="029bf-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="029bf-124">Quando la creazione di un controllo che può essere usata da una vista, questo controllo può essere specificato per l'elemento seguente: [Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="029bf-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="029bf-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="029bf-125">See Also</span></span>

[<span data-ttu-id="029bf-126">Elemento di controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="029bf-127">Elemento ExpressionBinding per CustomItem per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="029bf-128">Elemento ExpressionBinding per CustomItem per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="029bf-129">Elemento GroupBy per visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="029bf-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="029bf-130">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="029bf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
