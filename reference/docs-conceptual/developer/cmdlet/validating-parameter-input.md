---
title: Convalida input parametri | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363510"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="0745d-102">Convalida degli input dei parametri</span><span class="sxs-lookup"><span data-stu-id="0745d-102">Validating Parameter Input</span></span>

<span data-ttu-id="0745d-103">PowerShell può convalidare gli argomenti passati ai parametri dei cmdlet in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="0745d-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="0745d-104">PowerShell può convalidare la lunghezza, l'intervallo e il modello dei caratteri dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="0745d-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="0745d-105">Può convalidare il numero di argomenti disponibili (conteggio).</span><span class="sxs-lookup"><span data-stu-id="0745d-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="0745d-106">Queste regole di convalida sono definite dagli attributi di convalida dichiarati con l'attributo Parameter sulle proprietà pubbliche della classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0745d-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="0745d-107">Per convalidare un argomento di parametro, il runtime di PowerShell usa le informazioni fornite dagli attributi di convalida per confermare il valore del parametro prima dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0745d-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="0745d-108">Se l'input del parametro non è valido, l'utente riceve un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="0745d-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="0745d-109">Ogni parametro di convalida definisce una regola di convalida che viene applicata da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0745d-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="0745d-110">PowerShell applica le regole di convalida in base ai seguenti attributi.</span><span class="sxs-lookup"><span data-stu-id="0745d-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="0745d-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="0745d-111">ValidateCount</span></span>

<span data-ttu-id="0745d-112">Specifica il numero minimo e massimo di argomenti che un parametro può accettare.</span><span class="sxs-lookup"><span data-stu-id="0745d-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="0745d-113">Per altre informazioni, vedere [dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0745d-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="0745d-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="0745d-114">ValidateLength</span></span>

<span data-ttu-id="0745d-115">Specifica il numero minimo e massimo di caratteri nell'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="0745d-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="0745d-116">Per altre informazioni, vedere [dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0745d-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="0745d-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="0745d-117">ValidatePattern</span></span>

<span data-ttu-id="0745d-118">Specifica un'espressione regolare che convalida l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="0745d-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="0745d-119">Per altre informazioni, vedere [dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0745d-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="0745d-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="0745d-120">ValidateRange</span></span>

<span data-ttu-id="0745d-121">Specifica i valori minimo e massimo dell'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="0745d-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="0745d-122">Per altre informazioni, vedere [dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0745d-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="0745d-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="0745d-123">ValidateSet</span></span>

<span data-ttu-id="0745d-124">Specifica i valori validi per l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="0745d-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="0745d-125">Per altre informazioni, vedere [dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0745d-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0745d-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0745d-126">See Also</span></span>

[<span data-ttu-id="0745d-127">Come convalidare l'input del parametro</span><span class="sxs-lookup"><span data-stu-id="0745d-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="0745d-128">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0745d-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
