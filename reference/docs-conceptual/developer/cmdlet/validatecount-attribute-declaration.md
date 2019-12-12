---
title: Dichiarazione dell'attributo ValidateCount | Microsoft Docs
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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369230"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="3db44-102">Dichiarazione dell'attributo ValidateCount</span><span class="sxs-lookup"><span data-stu-id="3db44-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="3db44-103">L'attributo ValidateCount specifica il numero minimo e massimo di argomenti consentiti per un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3db44-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="3db44-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3db44-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="3db44-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3db44-105">Parameters</span></span>

<span data-ttu-id="3db44-106">`MinLength` ([System.Int32][]) obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3db44-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="3db44-107">Specifica il numero minimo di argomenti.</span><span class="sxs-lookup"><span data-stu-id="3db44-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="3db44-108">`MaxLength`([System.Int32][]) obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="3db44-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="3db44-109">Specifica il numero massimo di argomenti.</span><span class="sxs-lookup"><span data-stu-id="3db44-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="3db44-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3db44-110">Remarks</span></span>

- <span data-ttu-id="3db44-111">Per ulteriori informazioni su come dichiarare questo attributo, vedere [come convalidare un numero di argomenti][].</span><span class="sxs-lookup"><span data-stu-id="3db44-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="3db44-112">Quando questo attributo non viene richiamato, il parametro del cmdlet corrispondente può avere un numero qualsiasi di argomenti.</span><span class="sxs-lookup"><span data-stu-id="3db44-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="3db44-113">Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="3db44-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="3db44-114">I parametri dell'attributo `MinLength` e `MaxLength` non sono di tipo [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="3db44-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="3db44-115">Il valore del parametro dell'attributo `MaxLength` è minore del valore del parametro dell'attributo `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="3db44-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="3db44-116">L'attributo ValidateCount è definito dalla classe [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="3db44-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3db44-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3db44-117">See Also</span></span>

<span data-ttu-id="3db44-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="3db44-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="3db44-119">[Come convalidare un numero di argomenti][]</span><span class="sxs-lookup"><span data-stu-id="3db44-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="3db44-120">[Scrittura di un cmdlet di Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="3db44-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Come convalidare un numero di argomenti]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Scrittura di un cmdlet di Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
