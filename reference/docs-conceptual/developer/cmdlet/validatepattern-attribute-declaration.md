---
title: Dichiarazione dell'attributo ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369160"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="43828-102">Dichiarazione dell'attributo ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="43828-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="43828-103">L'attributo ValidatePattern specifica un modello di espressione regolare che convalida l'argomento di un parametro del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43828-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="43828-104">Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43828-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="43828-105">Quando ValidatePattern viene richiamato all'interno di un cmdlet, il runtime di Windows PowerShell converte l'argomento del parametro del cmdlet in una stringa e quindi confronta tale stringa con il modello fornito dall'attributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="43828-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="43828-106">Il cmdlet viene eseguito solo se la rappresentazione di stringa convertita dell'argomento e il criterio fornito corrispondono.</span><span class="sxs-lookup"><span data-stu-id="43828-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="43828-107">Se non corrispondono, viene generato un errore dal runtime di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43828-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="43828-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43828-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="43828-109">Parametri</span><span class="sxs-lookup"><span data-stu-id="43828-109">Parameters</span></span>

<span data-ttu-id="43828-110">`RegexString` ([System. String](/dotnet/api/System.String)) obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="43828-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="43828-111">Specifica un'espressione regolare che convalida l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="43828-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="43828-112">Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) parametro denominato facoltativo.</span><span class="sxs-lookup"><span data-stu-id="43828-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="43828-113">Specifica una combinazione bit per bit di flag [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) che specificano le opzioni di espressione regolare.</span><span class="sxs-lookup"><span data-stu-id="43828-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="43828-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="43828-114">Remarks</span></span>

- <span data-ttu-id="43828-115">Questo attributo può essere utilizzato una sola volta per ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="43828-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="43828-116">Per definire ulteriormente il modello, è possibile usare il parametro `Option` dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="43828-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="43828-117">Ad esempio, è possibile rendere la distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="43828-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="43828-118">Se questo attributo viene applicato a una raccolta, ogni elemento nella raccolta deve corrispondere al modello.</span><span class="sxs-lookup"><span data-stu-id="43828-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="43828-119">L'attributo ValidatePattern è definito dalla classe [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .</span><span class="sxs-lookup"><span data-stu-id="43828-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="43828-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43828-120">See Also</span></span>

[<span data-ttu-id="43828-121">System. Management. Automation. Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="43828-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="43828-122">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="43828-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
