---
title: Dichiarazione di attributo ValidateLength | Microsoft Docs
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
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855151"
---
# <a name="validatelength-attribute-declaration"></a>Dichiarazione dell'attributo ValidateLength

L'attributo ValidateLength specifica il numero minimo e massimo di caratteri per un argomento del cmdlet di parametro. Questo attributo può essere utilizzato anche dalle funzioni di Windows PowerShell.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametri

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) richiesto. Specifica il numero minimo di caratteri consentiti.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) richiesto. Specifica il numero massimo di caratteri consentiti.

## <a name="remarks"></a>Osservazioni

- Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare le regole di convalida Input](./how-to-validate-parameter-input.md).

- Quando questo attributo non viene utilizzato, l'argomento del parametro corrispondente può essere di qualsiasi lunghezza.

- Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:

    - Quando il valore della `MaxLength` parametro di attributo è minore del valore del `MinLength` parametro di attributo.

    - Quando il `MaxLength` parametro di attributo è impostato su 0.

    - Quando l'argomento non è una stringa.

- L'attributo ValidateLength è definito per il [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
