---
title: Come convalidare un numero di argomenti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859137"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="204cc-102">Come convalidare un numero di argomenti</span><span class="sxs-lookup"><span data-stu-id="204cc-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="204cc-103">In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare il numero di argomenti (numero) che accetta un parametro prima di eseguita il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="204cc-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="204cc-104">Per impostare questa regola di convalida, dichiarare l'attributo ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="204cc-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="204cc-105">Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="204cc-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="204cc-106">Per convalidare un numero di argomenti</span><span class="sxs-lookup"><span data-stu-id="204cc-106">To validate an argument count</span></span>

- <span data-ttu-id="204cc-107">Aggiungere l'attributo di convalida come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="204cc-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="204cc-108">Questo esempio specifica che il parametro può accettare un argomento o fino a tre argomenti.</span><span class="sxs-lookup"><span data-stu-id="204cc-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="204cc-109">Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="204cc-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="204cc-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="204cc-110">See Also</span></span>

[<span data-ttu-id="204cc-111">Dichiarazione di attributo ValidateCount</span><span class="sxs-lookup"><span data-stu-id="204cc-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="204cc-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="204cc-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
