---
title: Dichiarazione dell'attributo ValidateLength | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369180"
---
# <a name="validatelength-attribute-declaration"></a>Dichiarazione dell'attributo ValidateLength

L'attributo ValidateLength specifica il numero minimo e massimo di caratteri per un argomento di parametro del cmdlet. Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametri

`MinLength` ([System. Int32](/dotnet/api/System.Int32)) obbligatorio. Specifica il numero minimo di caratteri consentiti.

`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) obbligatorio. Specifica il numero massimo di caratteri consentiti.

## <a name="remarks"></a>Osservazioni

- Per ulteriori informazioni su come dichiarare questo attributo, vedere [How to declare input validation rules](./how-to-validate-parameter-input.md).

- Quando questo attributo non viene utilizzato, l'argomento del parametro corrispondente può essere di qualsiasi lunghezza.

- Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:

    - Se il valore del parametro dell'attributo `MaxLength` è minore del valore del parametro dell'attributo `MinLength`.

    - Quando il parametro dell'attributo `MaxLength` è impostato su 0.

    - Quando l'argomento non è una stringa.

- L'attributo ValidateLength è definito dalla classe [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
