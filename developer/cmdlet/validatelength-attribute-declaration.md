---
title: Dichiarazione di attributo ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855151"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="2a6ac-102">Dichiarazione dell'attributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="2a6ac-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="2a6ac-103">L'attributo ValidateLength specifica il numero minimo e massimo di caratteri per un argomento del cmdlet di parametro.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="2a6ac-104">Questo attributo può essere utilizzato anche dalle funzioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a6ac-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2a6ac-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="2a6ac-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="2a6ac-106">Parameters</span></span>

<span data-ttu-id="2a6ac-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="2a6ac-108">Specifica il numero minimo di caratteri consentiti.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="2a6ac-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="2a6ac-110">Specifica il numero massimo di caratteri consentiti.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a6ac-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2a6ac-111">Remarks</span></span>

- <span data-ttu-id="2a6ac-112">Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare le regole di convalida Input](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="2a6ac-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="2a6ac-113">Quando questo attributo non viene utilizzato, l'argomento del parametro corrispondente può essere di qualsiasi lunghezza.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="2a6ac-114">Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="2a6ac-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="2a6ac-115">Quando il valore della `MaxLength` parametro di attributo è minore del valore del `MinLength` parametro di attributo.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="2a6ac-116">Quando il `MaxLength` parametro di attributo è impostato su 0.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="2a6ac-117">Quando l'argomento non è una stringa.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-117">When the argument is not a string.</span></span>

- <span data-ttu-id="2a6ac-118">L'attributo ValidateLength è definito per il [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="2a6ac-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a6ac-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2a6ac-119">See Also</span></span>

[<span data-ttu-id="2a6ac-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="2a6ac-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="2a6ac-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a6ac-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
