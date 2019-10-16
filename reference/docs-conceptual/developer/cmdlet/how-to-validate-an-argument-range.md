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
# <a name="how-to-validate-an-argument-range"></a>Come convalidare un intervallo di argomenti

Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare i valori minimo e massimo dell'argomento del parametro prima dell'esecuzione del cmdlet. Questa regola di convalida viene impostata dichiarando l'attributo ValidateRange.

> [!NOTE]
> Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Per convalidare un intervallo di argomenti

- Aggiungere l'attributo ValidateRange come illustrato nel codice seguente. In questo esempio viene specificato un intervallo compreso tra 0 e 5 per il parametro `InputData`.

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

Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
