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
# <a name="how-to-validate-an-argument-set"></a>Come convalidare un set di argomenti

Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare l'argomento del parametro prima dell'esecuzione del cmdlet. Questa regola di convalida fornisce un set di valori validi per l'argomento parameter.

> [!NOTE]
> Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Per convalidare un set di argomenti

- Aggiungere l'attributo ValidateSet come illustrato nel codice seguente. In questo esempio viene specificato un set di tre valori possibili per il parametro `UserName`.

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

Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
