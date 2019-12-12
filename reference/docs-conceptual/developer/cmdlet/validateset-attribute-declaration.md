---
title: Dichiarazione dell'attributo ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364280"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="43007-102">Dichiarazione dell'attributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="43007-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="43007-103">L'attributo ValidateSetAttribute specifica un set di valori possibili per un argomento di parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43007-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="43007-104">Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43007-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="43007-105">Quando si specifica questo attributo, il runtime di Windows PowerShell determina se l'argomento fornito per il parametro del cmdlet corrisponde a un elemento nel set di elementi fornito.</span><span class="sxs-lookup"><span data-stu-id="43007-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="43007-106">Il cmdlet viene eseguito solo se l'argomento del parametro corrisponde a un elemento nel set.</span><span class="sxs-lookup"><span data-stu-id="43007-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="43007-107">Se non viene trovata alcuna corrispondenza, il runtime di Windows PowerShell genera un errore.</span><span class="sxs-lookup"><span data-stu-id="43007-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="43007-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43007-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="43007-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="43007-109">Parameters</span></span>

<span data-ttu-id="43007-110">`ValidValues` ([System. String](/dotnet/api/System.String)) obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="43007-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="43007-111">Specifica i valori validi per gli elementi di parametro.</span><span class="sxs-lookup"><span data-stu-id="43007-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="43007-112">Nell'esempio seguente viene illustrato come specificare un elemento o più elementi.</span><span class="sxs-lookup"><span data-stu-id="43007-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="43007-113">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="43007-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="43007-114">Il valore predefinito di `true` indica che il case viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="43007-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="43007-115">Il valore `false` rende il cmdlet con distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="43007-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="43007-116">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="43007-116">Remarks</span></span>

- <span data-ttu-id="43007-117">Questo attributo può essere utilizzato una sola volta per ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="43007-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="43007-118">Se il valore del parametro è una matrice, ogni elemento della matrice deve corrispondere a un elemento del set di attributi.</span><span class="sxs-lookup"><span data-stu-id="43007-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="43007-119">L'attributo ValidateSetAttribute è definito dalla classe [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="43007-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="43007-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43007-120">See Also</span></span>

[<span data-ttu-id="43007-121">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="43007-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="43007-122">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="43007-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
