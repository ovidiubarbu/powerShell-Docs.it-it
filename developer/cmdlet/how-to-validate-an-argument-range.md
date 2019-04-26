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
# <a name="how-to-validate-an-argument-range"></a>Come convalidare un intervallo di argomenti

In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare i valori minimi e massimo dell'argomento del parametro prima di eseguita il cmdlet. Per impostare questa regola di convalida, dichiarare l'attributo ValidateRange.

> [!NOTE]
> Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Per convalidare un intervallo di argomento

- Aggiungere l'attributo ValidateRange come illustrato nel codice seguente. Questo esempio viene specificato un intervallo da 0 a 5 per il `InputData` parametro.

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

Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
