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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365560"
---
# <a name="how-to-validate-an-argument-pattern"></a>Come convalidare un modello di argomenti

Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare il modello di caratteri dell'argomento del parametro prima dell'esecuzione del cmdlet. Questa regola di convalida viene impostata dichiarando l'attributo ValidatePattern.

> [!NOTE]
> Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Per convalidare un modello di argomento

- Aggiungere l'attributo Validate come illustrato nel codice seguente. In questo esempio viene specificato un modello di quattro cifre, in cui ogni cifra ha un valore compreso tra 0 e 9.

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

Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
