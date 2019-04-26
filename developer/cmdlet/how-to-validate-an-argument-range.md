---
title: Come convalidare un intervallo di argomento | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067791"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="3acd1-102">Come convalidare un intervallo di argomenti</span><span class="sxs-lookup"><span data-stu-id="3acd1-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="3acd1-103">In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare i valori minimi e massimo dell'argomento del parametro prima di eseguita il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3acd1-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="3acd1-104">Per impostare questa regola di convalida, dichiarare l'attributo ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="3acd1-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="3acd1-105">Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="3acd1-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="3acd1-106">Per convalidare un intervallo di argomento</span><span class="sxs-lookup"><span data-stu-id="3acd1-106">To validate an argument range</span></span>

- <span data-ttu-id="3acd1-107">Aggiungere l'attributo ValidateRange come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3acd1-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="3acd1-108">Questo esempio viene specificato un intervallo da 0 a 5 per il `InputData` parametro.</span><span class="sxs-lookup"><span data-stu-id="3acd1-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="3acd1-109">Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3acd1-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3acd1-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3acd1-110">See Also</span></span>

[<span data-ttu-id="3acd1-111">Dichiarazione di attributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="3acd1-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="3acd1-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3acd1-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
