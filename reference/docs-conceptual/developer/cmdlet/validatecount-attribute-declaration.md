---
title: Dichiarazione dell'attributo ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369230"
---
# <a name="validatecount-attribute-declaration"></a>Dichiarazione dell'attributo ValidateCount

L'attributo ValidateCount specifica il numero minimo e massimo di argomenti consentiti per un parametro del cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametri

`MinLength` ([System. Int32][]) obbligatorio. Specifica il numero minimo di argomenti.

`MaxLength` ([System. Int32][]) obbligatorio. Specifica il numero massimo di argomenti.

## <a name="remarks"></a>Osservazioni

- Per ulteriori informazioni su come dichiarare questo attributo, vedere [come convalidare un numero di argomenti][].

- Quando questo attributo non viene richiamato, il parametro del cmdlet corrispondente può avere un numero qualsiasi di argomenti.

- Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:

    - I parametri dell'attributo `MinLength` e `MaxLength` non sono di tipo [System. Int32][].

    - Il valore del parametro dell'attributo `MaxLength` è minore del valore del parametro dell'attributo `MinLength`.

- L'attributo ValidateCount è definito dalla classe [System. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. ValidateCountAttribute][]

[Come convalidare un numero di argomenti][]

[Scrittura di un cmdlet di Windows PowerShell][]

[Come convalidare un numero di argomenti]: how-to-validate-an-argument-count.md
[Scrittura di un cmdlet di Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
