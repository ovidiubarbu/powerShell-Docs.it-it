---
title: Come convalidare un set di argomenti | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365510"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="d0f7e-102">Come convalidare un set di argomenti</span><span class="sxs-lookup"><span data-stu-id="d0f7e-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="d0f7e-103">Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare l'argomento del parametro prima dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d0f7e-104">Questa regola di convalida fornisce un set di valori validi per l'argomento parameter.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="d0f7e-105">Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="d0f7e-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="d0f7e-106">Per convalidare un set di argomenti</span><span class="sxs-lookup"><span data-stu-id="d0f7e-106">To validate an argument set</span></span>

- <span data-ttu-id="d0f7e-107">Aggiungere l'attributo ValidateSet come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="d0f7e-108">In questo esempio viene specificato un set di tre valori possibili per il parametro `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d0f7e-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="d0f7e-109">Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d0f7e-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f7e-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d0f7e-110">See Also</span></span>

[<span data-ttu-id="d0f7e-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="d0f7e-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="d0f7e-112">Dichiarazione dell'attributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="d0f7e-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="d0f7e-113">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0f7e-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
