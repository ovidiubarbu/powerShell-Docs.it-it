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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857127"
---
# <a name="how-to-validate-the-argument-length"></a>Come convalidare la lunghezza degli argomenti

In questo esempio viene illustrato come specificare una regola di convalida che il runtime di Windows PowerShell è possibile usare per controllare il numero di caratteri (lunghezza) dell'argomento del parametro prima di eseguita il cmdlet. Per impostare questa regola di convalida, dichiarare l'attributo ValidateLength.

> [!NOTE]
> Per altre informazioni sulla classe che definisce questo attributo, vedere [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Per convalidare la lunghezza dell'argomento

- Aggiungere l'attributo di convalida come illustrato nel codice seguente. Questo esempio specifica che la lunghezza dell'argomento deve avere una lunghezza pari a 0 a 10 caratteri.

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

Per altre informazioni su come dichiarare questo attributo, vedere [dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
