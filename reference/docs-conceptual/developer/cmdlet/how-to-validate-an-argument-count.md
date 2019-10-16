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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365530"
---
# <a name="how-to-validate-an-argument-count"></a>Come convalidare un numero di argomenti

Questo esempio illustra come specificare una regola di convalida che può essere usata dal runtime di Windows PowerShell per controllare il numero di argomenti (conteggio) accettati da un parametro prima dell'esecuzione del cmdlet. Questa regola di convalida viene impostata dichiarando l'attributo ValidateCount.

> [!NOTE]
> Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Per convalidare un numero di argomenti

- Aggiungere l'attributo Validate come illustrato nel codice seguente. Questo esempio specifica che il parametro accetterà un argomento o un numero di tre argomenti.

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

Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
