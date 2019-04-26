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
# <a name="how-to-validate-an-argument-set"></a>Come convalidare un set di argomenti

In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare l'argomento del parametro prima di eseguita il cmdlet. Questa regola di convalida fornisce un set di valori validi per l'argomento del parametro.

> [!NOTE]
> Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Per convalidare un set di argomenti

- Aggiungere l'attributo ValidateSet come illustrato nel codice seguente. In questo esempio specifica un set di tre valori possibili per il `UserName` parametro.

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

Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
