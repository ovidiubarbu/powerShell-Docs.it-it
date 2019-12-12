---
title: Come convalidare un modello di argomento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365560"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="b8713-102">Come convalidare un modello di argomenti</span><span class="sxs-lookup"><span data-stu-id="b8713-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="b8713-103">Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare il modello di caratteri dell'argomento del parametro prima dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8713-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="b8713-104">Questa regola di convalida viene impostata dichiarando l'attributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="b8713-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="b8713-105">Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="b8713-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="b8713-106">Per convalidare un modello di argomento</span><span class="sxs-lookup"><span data-stu-id="b8713-106">To validate an argument pattern</span></span>

- <span data-ttu-id="b8713-107">Aggiungere l'attributo Validate come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="b8713-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="b8713-108">In questo esempio viene specificato un modello di quattro cifre, in cui ogni cifra ha un valore compreso tra 0 e 9.</span><span class="sxs-lookup"><span data-stu-id="b8713-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="b8713-109">Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b8713-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8713-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b8713-110">See Also</span></span>

[<span data-ttu-id="b8713-111">Dichiarazione dell'attributo ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="b8713-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="b8713-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8713-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
