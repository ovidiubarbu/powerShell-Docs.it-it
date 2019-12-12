---
title: Come convalidare la lunghezza dell'argomento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365490"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="957b8-102">Come convalidare la lunghezza degli argomenti</span><span class="sxs-lookup"><span data-stu-id="957b8-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="957b8-103">Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare il numero di caratteri (la lunghezza) dell'argomento del parametro prima dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="957b8-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="957b8-104">Questa regola di convalida viene impostata dichiarando l'attributo ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="957b8-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="957b8-105">Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="957b8-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="957b8-106">Per convalidare la lunghezza dell'argomento</span><span class="sxs-lookup"><span data-stu-id="957b8-106">To validate the argument length</span></span>

- <span data-ttu-id="957b8-107">Aggiungere l'attributo Validate come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="957b8-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="957b8-108">Questo esempio specifica che la lunghezza dell'argomento deve avere una lunghezza compresa tra 0 e 10 caratteri.</span><span class="sxs-lookup"><span data-stu-id="957b8-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="957b8-109">Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="957b8-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="957b8-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="957b8-110">See Also</span></span>

[<span data-ttu-id="957b8-111">Dichiarazione dell'attributo ValidateLength</span><span class="sxs-lookup"><span data-stu-id="957b8-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="957b8-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="957b8-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
