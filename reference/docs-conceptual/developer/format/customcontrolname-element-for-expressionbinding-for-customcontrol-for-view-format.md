---
title: Elemento CustomControlName per Expression per CustomControl per View (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364110"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="657dc-102">Elemento CustomControlName per ExpressionBinding per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="657dc-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="657dc-103">Specifica il nome di un controllo comune o di un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="657dc-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="657dc-104">Questo elemento viene utilizzato quando si definisce una visualizzazione controlli personalizzata.</span><span class="sxs-lookup"><span data-stu-id="657dc-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="657dc-105">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento CustomControl per View (Format) elemento CustomEntries per CustomControl per la visualizzazione (Format) CustomEntry elemento per CustomEntries per View (Format) CustomItem Elemento per CustomEntry per l'elemento Expressiongroup per la visualizzazione (Format) per CustomItem (Format) CustomControlName per l'associazione di espressioni per CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="657dc-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="657dc-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="657dc-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="657dc-107">Attributes and Elements</span></span>

<span data-ttu-id="657dc-108">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e l'elemento padre dell'elemento `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="657dc-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="657dc-109">Attributi</span><span class="sxs-lookup"><span data-stu-id="657dc-109">Attributes</span></span>

<span data-ttu-id="657dc-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="657dc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="657dc-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="657dc-111">Child Elements</span></span>

<span data-ttu-id="657dc-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="657dc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="657dc-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="657dc-113">Parent Elements</span></span>

|<span data-ttu-id="657dc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="657dc-114">Element</span></span>|<span data-ttu-id="657dc-115">Description</span><span class="sxs-lookup"><span data-stu-id="657dc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="657dc-116">Elemento expressiongroup per CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="657dc-117">Definisce i dati visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="657dc-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="657dc-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="657dc-118">Text Value</span></span>

<span data-ttu-id="657dc-119">Specificare il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="657dc-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="657dc-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="657dc-120">Remarks</span></span>

<span data-ttu-id="657dc-121">È possibile creare controlli comuni che possono essere utilizzati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere utilizzati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="657dc-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="657dc-122">I nomi di questi controlli sono specificati dagli elementi seguenti.</span><span class="sxs-lookup"><span data-stu-id="657dc-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="657dc-123">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="657dc-124">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="657dc-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="657dc-125">See Also</span></span>

[<span data-ttu-id="657dc-126">Elemento Name per il controllo per i controlli per la configurazione (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="657dc-127">Elemento Name per il controllo per i controlli per la visualizzazione (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="657dc-128">Elemento expressiongroup per CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="657dc-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="657dc-129">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="657dc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
