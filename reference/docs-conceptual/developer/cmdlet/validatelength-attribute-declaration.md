---
title: Dichiarazione dell'attributo ValidateLength | Microsoft Docs
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
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369180"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="ae4e5-102">Dichiarazione dell'attributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="ae4e5-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="ae4e5-103">L'attributo ValidateLength specifica il numero minimo e massimo di caratteri per un argomento di parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="ae4e5-104">Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae4e5-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ae4e5-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ae4e5-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="ae4e5-106">Parameters</span></span>

<span data-ttu-id="ae4e5-107">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ae4e5-108">Specifica il numero minimo di caratteri consentiti.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="ae4e5-109">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ae4e5-110">Specifica il numero massimo di caratteri consentiti.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae4e5-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ae4e5-111">Remarks</span></span>

- <span data-ttu-id="ae4e5-112">Per ulteriori informazioni su come dichiarare questo attributo, vedere [How to declare input validation rules](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="ae4e5-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="ae4e5-113">Quando questo attributo non viene utilizzato, l'argomento del parametro corrispondente può essere di qualsiasi lunghezza.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="ae4e5-114">Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="ae4e5-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="ae4e5-115">Se il valore del parametro dell'attributo `MaxLength` è minore del valore del parametro dell'attributo `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="ae4e5-116">Quando il parametro dell'attributo `MaxLength` è impostato su 0.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="ae4e5-117">Quando l'argomento non è una stringa.</span><span class="sxs-lookup"><span data-stu-id="ae4e5-117">When the argument is not a string.</span></span>

- <span data-ttu-id="ae4e5-118">L'attributo ValidateLength è definito dalla classe [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ae4e5-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae4e5-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ae4e5-119">See Also</span></span>

[<span data-ttu-id="ae4e5-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="ae4e5-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="ae4e5-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae4e5-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
