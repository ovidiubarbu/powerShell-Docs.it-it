---
title: Come convalidare un intervallo di argomenti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365520"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="8d16b-102">Come convalidare un intervallo di argomenti</span><span class="sxs-lookup"><span data-stu-id="8d16b-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="8d16b-103">Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare i valori minimo e massimo dell'argomento del parametro prima dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d16b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="8d16b-104">Questa regola di convalida viene impostata dichiarando l'attributo ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="8d16b-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="8d16b-105">Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="8d16b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="8d16b-106">Per convalidare un intervallo di argomenti</span><span class="sxs-lookup"><span data-stu-id="8d16b-106">To validate an argument range</span></span>

- <span data-ttu-id="8d16b-107">Aggiungere l'attributo ValidateRange come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="8d16b-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="8d16b-108">In questo esempio viene specificato un intervallo compreso tra 0 e 5 per il parametro `InputData`.</span><span class="sxs-lookup"><span data-stu-id="8d16b-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="8d16b-109">Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8d16b-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d16b-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8d16b-110">See Also</span></span>

[<span data-ttu-id="8d16b-111">Dichiarazione dell'attributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="8d16b-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="8d16b-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d16b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
