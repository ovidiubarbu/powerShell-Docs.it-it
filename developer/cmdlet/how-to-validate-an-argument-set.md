---
title: Come convalidare un Set di argomenti | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067716"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="3a6d2-102">Come convalidare un set di argomenti</span><span class="sxs-lookup"><span data-stu-id="3a6d2-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="3a6d2-103">In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare l'argomento del parametro prima di eseguita il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="3a6d2-104">Questa regola di convalida fornisce un set di valori validi per l'argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="3a6d2-105">Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="3a6d2-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="3a6d2-106">Per convalidare un set di argomenti</span><span class="sxs-lookup"><span data-stu-id="3a6d2-106">To validate an argument set</span></span>

- <span data-ttu-id="3a6d2-107">Aggiungere l'attributo ValidateSet come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="3a6d2-108">In questo esempio specifica un set di tre valori possibili per il `UserName` parametro.</span><span class="sxs-lookup"><span data-stu-id="3a6d2-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="3a6d2-109">Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="3a6d2-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a6d2-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3a6d2-110">See Also</span></span>

[<span data-ttu-id="3a6d2-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="3a6d2-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="3a6d2-112">Dichiarazione di attributo ValidateSet</span><span class="sxs-lookup"><span data-stu-id="3a6d2-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="3a6d2-113">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a6d2-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
