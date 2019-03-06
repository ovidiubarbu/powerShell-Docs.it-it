---
title: Convalida Input parametro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429840"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="17029-102">Convalida degli input dei parametri</span><span class="sxs-lookup"><span data-stu-id="17029-102">Validating Parameter Input</span></span>

<span data-ttu-id="17029-103">PowerShell è possibile convalidare gli argomenti passati ai parametri del cmdlet in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="17029-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="17029-104">PowerShell è possibile convalidare la lunghezza dell'intervallo e il modello di caratteri dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="17029-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="17029-105">È possibile convalidare il numero di argomenti disponibili (numero).</span><span class="sxs-lookup"><span data-stu-id="17029-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="17029-106">Queste regole di convalida sono definite da attributi di convalida che vengono dichiarati con l'attributo di parametro nelle proprietà pubbliche della classe del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17029-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="17029-107">Per convalidare un argomento del parametro, il runtime di PowerShell Usa le informazioni fornite dagli attributi di convalida per confermare che il valore del parametro prima di eseguita il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17029-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="17029-108">Se l'input del parametro non è valido, l'utente riceve un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="17029-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="17029-109">Parametro ogni convalida definisce una regola di convalida applicato da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17029-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="17029-110">PowerShell consente di applicare le regole di convalida in base agli attributi seguenti.</span><span class="sxs-lookup"><span data-stu-id="17029-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="17029-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="17029-111">ValidateCount</span></span>

<span data-ttu-id="17029-112">Specifica il numero minimo e massimo di argomenti che può accettare un parametro.</span><span class="sxs-lookup"><span data-stu-id="17029-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="17029-113">Per altre informazioni, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="17029-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="17029-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="17029-114">ValidateLength</span></span>

<span data-ttu-id="17029-115">Specifica il numero minimo e massimo di caratteri nell'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="17029-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="17029-116">Per altre informazioni, vedere [dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="17029-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="17029-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="17029-117">ValidatePattern</span></span>

<span data-ttu-id="17029-118">Specifica un'espressione regolare che convalida l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="17029-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="17029-119">Per altre informazioni, vedere [dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="17029-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="17029-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="17029-120">ValidateRange</span></span>

<span data-ttu-id="17029-121">Specifica i valori minimi e massimo dell'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="17029-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="17029-122">Per altre informazioni, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="17029-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="17029-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="17029-123">ValidateSet</span></span>

<span data-ttu-id="17029-124">Specifica i valori validi per l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="17029-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="17029-125">Per altre informazioni, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="17029-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17029-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="17029-126">See Also</span></span>

[<span data-ttu-id="17029-127">Come convalidare l'Input del parametro</span><span class="sxs-lookup"><span data-stu-id="17029-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="17029-128">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17029-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
