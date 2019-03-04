---
title: Dichiarazione di attributo ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859157"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="f13a3-102">Dichiarazione dell'attributo ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f13a3-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="f13a3-103">L'attributo ValidateCount specifica il numero minimo e massimo di argomenti è consentito per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f13a3-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="f13a3-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f13a3-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="f13a3-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f13a3-105">Parameters</span></span>

<span data-ttu-id="f13a3-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="f13a3-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="f13a3-107">Specifica il numero minimo di argomenti.</span><span class="sxs-lookup"><span data-stu-id="f13a3-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="f13a3-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="f13a3-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="f13a3-109">Specifica il numero massimo di argomenti.</span><span class="sxs-lookup"><span data-stu-id="f13a3-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="f13a3-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f13a3-110">Remarks</span></span>

- <span data-ttu-id="f13a3-111">Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare le regole di convalida Input](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="f13a3-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="f13a3-112">Quando questo attributo non viene richiamato, il parametro di cmdlet corrispondente può avere qualsiasi numero di argomenti.</span><span class="sxs-lookup"><span data-stu-id="f13a3-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="f13a3-113">Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f13a3-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="f13a3-114">Il `MinLength` e `MaxLength` parametri dell'attributo non sono di tipo [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="f13a3-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="f13a3-115">Il valore della `MaxLength` parametro di attributo è minore del valore del `MinLength` parametro di attributo.</span><span class="sxs-lookup"><span data-stu-id="f13a3-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="f13a3-116">L'attributo ValidateCount è definito per il [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.</span><span class="sxs-lookup"><span data-stu-id="f13a3-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f13a3-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f13a3-117">See Also</span></span>

[<span data-ttu-id="f13a3-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="f13a3-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="f13a3-119">Come dichiarare le regole di convalida dell'Input</span><span class="sxs-lookup"><span data-stu-id="f13a3-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="f13a3-120">Come dichiarare le regole di convalida dell'Input</span><span class="sxs-lookup"><span data-stu-id="f13a3-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="f13a3-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f13a3-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
