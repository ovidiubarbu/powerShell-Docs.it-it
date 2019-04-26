---
title: Tipi di attributo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068659"
---
# <a name="attribute-types"></a><span data-ttu-id="6b55f-102">Tipi di attributo</span><span class="sxs-lookup"><span data-stu-id="6b55f-102">Attribute Types</span></span>

<span data-ttu-id="6b55f-103">Gli attributi di cmdlet possono essere raggruppati per funzionalità.</span><span class="sxs-lookup"><span data-stu-id="6b55f-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="6b55f-104">Le sezioni seguenti descrivono gli attributi disponibili e descrivono l'azione di runtime quando viene richiamato l'attributo.</span><span class="sxs-lookup"><span data-stu-id="6b55f-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="6b55f-105">Attributi dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b55f-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="6b55f-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b55f-106">Cmdlet</span></span>

<span data-ttu-id="6b55f-107">Identifica una classe .NET Framework come un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b55f-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="6b55f-108">Si tratta dell'attributo di base obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="6b55f-108">This is the required base attribute.</span></span>
<span data-ttu-id="6b55f-109">Per altre informazioni, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="6b55f-110">Attributi dei parametri</span><span class="sxs-lookup"><span data-stu-id="6b55f-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="6b55f-111">Parametro</span><span class="sxs-lookup"><span data-stu-id="6b55f-111">Parameter</span></span>

<span data-ttu-id="6b55f-112">Identifica una proprietà pubblica della classe cmdlet come un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b55f-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="6b55f-113">Per altre informazioni, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="6b55f-114">Alias</span><span class="sxs-lookup"><span data-stu-id="6b55f-114">Alias</span></span>

<span data-ttu-id="6b55f-115">Specifica uno o più alias per un parametro.</span><span class="sxs-lookup"><span data-stu-id="6b55f-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="6b55f-116">Per altre informazioni, vedere [dichiarazione di attributo Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="6b55f-117">Attributi di convalida di argomenti</span><span class="sxs-lookup"><span data-stu-id="6b55f-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="6b55f-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="6b55f-118">ValidateCount</span></span>

<span data-ttu-id="6b55f-119">Specifica il numero minimo e massimo di argomenti che sono consentite per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b55f-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="6b55f-120">Per altre informazioni, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="6b55f-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="6b55f-121">ValidateLength</span></span>

<span data-ttu-id="6b55f-122">Specifica un numero minimo e massimo di caratteri per un argomento del cmdlet di parametro.</span><span class="sxs-lookup"><span data-stu-id="6b55f-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="6b55f-123">Per altre informazioni, vedere [dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="6b55f-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="6b55f-124">ValidatePattern</span></span>

<span data-ttu-id="6b55f-125">Specifica un criterio di espressione regolare che deve corrispondere l'argomento del parametro di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b55f-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="6b55f-126">Per altre informazioni, vedere [dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="6b55f-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="6b55f-127">ValidateRange</span></span>

<span data-ttu-id="6b55f-128">Specifica i valori minimi e massimo per un argomento del cmdlet di parametro.</span><span class="sxs-lookup"><span data-stu-id="6b55f-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="6b55f-129">Per altre informazioni, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="6b55f-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="6b55f-130">ValidateSet</span></span>

<span data-ttu-id="6b55f-131">Specifica un set di valori validi per l'argomento del parametro di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b55f-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="6b55f-132">Per altre informazioni, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="6b55f-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b55f-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6b55f-133">See Also</span></span>

[<span data-ttu-id="6b55f-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6b55f-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
