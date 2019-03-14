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
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794442"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="7ad52-102">Dichiarazione dell'attributo ValidateCount</span><span class="sxs-lookup"><span data-stu-id="7ad52-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="7ad52-103">L'attributo ValidateCount specifica il numero minimo e massimo di argomenti è consentito per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ad52-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ad52-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7ad52-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="7ad52-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="7ad52-105">Parameters</span></span>

<span data-ttu-id="7ad52-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="7ad52-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="7ad52-107">Specifica il numero minimo di argomenti.</span><span class="sxs-lookup"><span data-stu-id="7ad52-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="7ad52-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="7ad52-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="7ad52-109">Specifica il numero massimo di argomenti.</span><span class="sxs-lookup"><span data-stu-id="7ad52-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ad52-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7ad52-110">Remarks</span></span>

- <span data-ttu-id="7ad52-111">Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare le regole di convalida Input](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="7ad52-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="7ad52-112">Quando questo attributo non viene richiamato, il parametro di cmdlet corrispondente può avere qualsiasi numero di argomenti.</span><span class="sxs-lookup"><span data-stu-id="7ad52-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="7ad52-113">Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7ad52-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="7ad52-114">Il `MinLength` e `MaxLength` parametri dell'attributo non sono di tipo [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="7ad52-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="7ad52-115">Il valore della `MaxLength` parametro di attributo è minore del valore del `MinLength` parametro di attributo.</span><span class="sxs-lookup"><span data-stu-id="7ad52-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="7ad52-116">L'attributo ValidateCount è definito per il [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.</span><span class="sxs-lookup"><span data-stu-id="7ad52-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ad52-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7ad52-117">See Also</span></span>

[<span data-ttu-id="7ad52-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="7ad52-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="7ad52-119">Come dichiarare le regole di convalida dell'Input</span><span class="sxs-lookup"><span data-stu-id="7ad52-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="7ad52-120">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ad52-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
