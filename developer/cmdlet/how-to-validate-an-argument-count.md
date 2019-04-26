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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067808"
---
# <a name="how-to-validate-an-argument-count"></a>Come convalidare un numero di argomenti

In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare il numero di argomenti (numero) che accetta un parametro prima di eseguita il cmdlet. Per impostare questa regola di convalida, dichiarare l'attributo ValidateCount.

> [!NOTE]
> Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Per convalidare un numero di argomenti

- Aggiungere l'attributo di convalida come illustrato nel codice seguente. Questo esempio specifica che il parametro può accettare un argomento o fino a tre argomenti.

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

Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
