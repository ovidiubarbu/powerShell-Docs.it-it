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
# <a name="how-to-validate-the-argument-length"></a>Come convalidare la lunghezza degli argomenti

Questo esempio illustra come specificare una regola di convalida che il runtime di Windows PowerShell può usare per controllare il numero di caratteri (la lunghezza) dell'argomento del parametro prima dell'esecuzione del cmdlet. Questa regola di convalida viene impostata dichiarando l'attributo ValidateLength.

> [!NOTE]
> Per ulteriori informazioni sulla classe che definisce questo attributo, vedere [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Per convalidare la lunghezza dell'argomento

- Aggiungere l'attributo Validate come illustrato nel codice seguente. Questo esempio specifica che la lunghezza dell'argomento deve avere una lunghezza compresa tra 0 e 10 caratteri.

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

Per ulteriori informazioni su come dichiarare questo attributo, vedere [dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Dichiarazione dell'attributo ValidateLength](./validatelength-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
