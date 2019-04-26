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
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067162"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="fcb8d-102">Dichiarazione dell'attributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="fcb8d-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="fcb8d-103">L'attributo ValidateLength specifica il numero minimo e massimo di caratteri per un argomento del cmdlet di parametro.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="fcb8d-104">Questo attributo può essere utilizzato anche dalle funzioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcb8d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="fcb8d-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="fcb8d-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="fcb8d-106">Parameters</span></span>

<span data-ttu-id="fcb8d-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="fcb8d-108">Specifica il numero minimo di caratteri consentiti.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="fcb8d-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) richiesto.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="fcb8d-110">Specifica il numero massimo di caratteri consentiti.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcb8d-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="fcb8d-111">Remarks</span></span>

- <span data-ttu-id="fcb8d-112">Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare le regole di convalida Input](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="fcb8d-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="fcb8d-113">Quando questo attributo non viene utilizzato, l'argomento del parametro corrispondente può essere di qualsiasi lunghezza.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="fcb8d-114">Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="fcb8d-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="fcb8d-115">Quando il valore della `MaxLength` parametro di attributo è minore del valore del `MinLength` parametro di attributo.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="fcb8d-116">Quando il `MaxLength` parametro di attributo è impostato su 0.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="fcb8d-117">Quando l'argomento non è una stringa.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-117">When the argument is not a string.</span></span>

- <span data-ttu-id="fcb8d-118">L'attributo ValidateLength è definito per il [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="fcb8d-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb8d-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fcb8d-119">See Also</span></span>

[<span data-ttu-id="fcb8d-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="fcb8d-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="fcb8d-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fcb8d-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
