---
title: Dichiarazione di attributo ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857037"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="53277-102">Dichiarazione dell'attributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="53277-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="53277-103">L'attributo ValidateRange specifica i valori minimi e massimo (intervallo) per l'argomento del parametro di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53277-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="53277-104">Questo attributo può essere utilizzato anche dalle funzioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53277-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="53277-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="53277-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="53277-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="53277-106">Parameters</span></span>

<span data-ttu-id="53277-107">`MinRange` ([System. Object](/dotnet/api/system.object)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="53277-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="53277-108">Specifica il valore minimo consentito.</span><span class="sxs-lookup"><span data-stu-id="53277-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="53277-109">`MaxRange` ([System. Object](/dotnet/api/system.object)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="53277-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="53277-110">Specifica il valore massimo consentito.</span><span class="sxs-lookup"><span data-stu-id="53277-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="53277-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="53277-111">Remarks</span></span>

- <span data-ttu-id="53277-112">Il runtime di Windows PowerShell genera un errore di costruzione quando il valore della `MinRange` è maggiore del valore del parametro di `MaxRange` parametro.</span><span class="sxs-lookup"><span data-stu-id="53277-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="53277-113">Il runtime di Windows PowerShell genera un errore di convalida nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="53277-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="53277-114">Quando il valore dell'argomento è inferiore al `MinRange` limite o maggiore di `MaxRange` limite.</span><span class="sxs-lookup"><span data-stu-id="53277-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="53277-115">Quando l'argomento non è dello stesso tipo di `MinRange` e il `MaxRange` parametri.</span><span class="sxs-lookup"><span data-stu-id="53277-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="53277-116">L'attributo ValidateRange è definito per il [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="53277-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="53277-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53277-117">See Also</span></span>

[<span data-ttu-id="53277-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="53277-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="53277-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="53277-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
