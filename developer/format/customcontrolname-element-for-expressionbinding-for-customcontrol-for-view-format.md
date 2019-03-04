---
title: Elemento CustomControlName per ExpressionBinding per CustomControl per visualizzazione (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860437"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="f6cfb-102">Elemento CustomControlName per ExpressionBinding per CustomControl per View (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="f6cfb-103">Specifica il nome di un controllo comune o un controllo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="f6cfb-104">Questo elemento viene usato quando si definisce una vista di controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f6cfb-105">Elemento di CustomControl elemento (formato) per la visualizzazione elemento ViewDefinitions (formato) configurazione elemento (formato) elemento di visualizzazione (formato) CustomEntries per CustomControl elemento di visualizzazione (formato) CustomEntry per CustomEntries per CustomItem visualizzazione (formato) Elemento per CustomEntry per visualizzazione (formato) ExpressionBinding elemento per elemento CustomControlName CustomItem (formato) per l'associazione di espressioni per CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6cfb-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f6cfb-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6cfb-107">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f6cfb-107">Attributes and Elements</span></span>

<span data-ttu-id="f6cfb-108">Le sezioni seguenti descrivono gli attributi e gli elementi figlio dell'elemento padre del `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6cfb-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f6cfb-109">Attributes</span></span>

<span data-ttu-id="f6cfb-110">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6cfb-111">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f6cfb-111">Child Elements</span></span>

<span data-ttu-id="f6cfb-112">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f6cfb-113">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f6cfb-113">Parent Elements</span></span>

|<span data-ttu-id="f6cfb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6cfb-114">Element</span></span>|<span data-ttu-id="f6cfb-115">Description</span><span class="sxs-lookup"><span data-stu-id="f6cfb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6cfb-116">Elemento ExpressionBinding per CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f6cfb-117">Definisce i dati che vengano visualizzati dal controllo.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f6cfb-118">Valore di testo</span><span class="sxs-lookup"><span data-stu-id="f6cfb-118">Text Value</span></span>

<span data-ttu-id="f6cfb-119">Specificare il nome del controllo.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6cfb-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f6cfb-120">Remarks</span></span>

<span data-ttu-id="f6cfb-121">È possibile creare controlli comuni che possono essere usati da tutte le visualizzazioni di un file di formattazione ed è possibile creare controlli di visualizzazione che possono essere usati da una visualizzazione specifica.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="f6cfb-122">I nomi di questi controlli vengono specificati dagli elementi seguenti.</span><span class="sxs-lookup"><span data-stu-id="f6cfb-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="f6cfb-123">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="f6cfb-124">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="f6cfb-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f6cfb-125">See Also</span></span>

[<span data-ttu-id="f6cfb-126">Elemento Name per il controllo per i controlli per la configurazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="f6cfb-127">Elemento Name per il controllo per i controlli per la visualizzazione (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f6cfb-128">Elemento ExpressionBinding per CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f6cfb-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f6cfb-129">La scrittura di un File di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6cfb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
