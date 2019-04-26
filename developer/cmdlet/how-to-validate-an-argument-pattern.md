---
title: Come convalidare un modello di argomento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067774"
---
# <a name="how-to-validate-an-argument-pattern"></a>Come convalidare un modello di argomenti

In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare il modello di caratteri dell'argomento del parametro prima di eseguita il cmdlet. Per impostare questa regola di convalida, dichiarare l'attributo ValidatePattern.

> [!NOTE]
> Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Per convalidare un modello di argomento

- Aggiungere l'attributo di convalida come illustrato nel codice seguente. Questo esempio specifica una serie di quattro cifre, dove ogni cifra è un valore compreso tra 0 e 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
