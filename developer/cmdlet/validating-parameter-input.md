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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858847"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="c51f4-102">Convalida degli input dei parametri</span><span class="sxs-lookup"><span data-stu-id="c51f4-102">Validating Parameter Input</span></span>

<span data-ttu-id="c51f4-103">Windows PowerShell è possibile convalidare gli argomenti passati ai parametri del cmdlet in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="c51f4-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="c51f4-104">Windows PowerShell è possibile convalidare la lunghezza dell'intervallo e il modello di caratteri dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="c51f4-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="c51f4-105">È possibile convalidare il numero di argomenti disponibili (numero).</span><span class="sxs-lookup"><span data-stu-id="c51f4-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="c51f4-106">Queste regole di convalida sono definite da attributi di convalida che vengono dichiarati con l'attributo di parametro nelle proprietà pubbliche della classe del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c51f4-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="c51f4-107">Per convalidare un argomento del parametro, il runtime di Windows PowerShell Usa le informazioni fornite dagli attributi di convalida per confermare che il valore del parametro prima di eseguita il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c51f4-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="c51f4-108">Se l'input del parametro non è valido, l'utente riceve un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="c51f4-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="c51f4-109">Parametro ogni convalida definisce una regola di convalida applicato da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c51f4-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="c51f4-110">Windows PowerShell consente di applicare le regole di convalida in base agli attributi seguenti.</span><span class="sxs-lookup"><span data-stu-id="c51f4-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="c51f4-111">ValidateCount specifica il numero minimo e massimo di argomenti che può accettare un parametro.</span><span class="sxs-lookup"><span data-stu-id="c51f4-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="c51f4-112">Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c51f4-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="c51f4-113">ValidateLength specifica il numero minimo e massimo di caratteri nell'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="c51f4-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="c51f4-114">Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c51f4-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="c51f4-115">ValidatePattern consente di specificare un'espressione regolare che convalida l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="c51f4-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="c51f4-116">Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c51f4-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="c51f4-117">ValidateRange specifica i valori minimi e massimo dell'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="c51f4-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="c51f4-118">Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c51f4-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="c51f4-119">ValidateSet specifica i valori validi per l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="c51f4-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="c51f4-120">Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c51f4-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c51f4-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c51f4-121">See Also</span></span>

[<span data-ttu-id="c51f4-122">Come convalidare l'Input del parametro</span><span class="sxs-lookup"><span data-stu-id="c51f4-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="c51f4-123">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c51f4-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
