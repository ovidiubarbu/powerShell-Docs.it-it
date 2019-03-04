---
title: Dichiarazione di attributo ValidateCount | Microsoft Docs
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
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859157"
---
# <a name="validatecount-attribute-declaration"></a>Dichiarazione dell'attributo ValidateCount

L'attributo ValidateCount specifica il numero minimo e massimo di argomenti è consentito per un parametro del cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parametri

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) richiesto. Specifica il numero minimo di argomenti.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) richiesto. Specifica il numero massimo di argomenti.

## <a name="remarks"></a>Osservazioni

- Per altre informazioni su come dichiarare questo attributo, vedere [come dichiarare le regole di convalida Input](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Quando questo attributo non viene richiamato, il parametro di cmdlet corrispondente può avere qualsiasi numero di argomenti.

- Il runtime di Windows PowerShell genera un errore nelle condizioni seguenti:

    - Il `MinLength` e `MaxLength` parametri dell'attributo non sono di tipo [System.Int32](/dotnet/api/System.Int32).

    - Il valore della `MaxLength` parametro di attributo è minore del valore del `MinLength` parametro di attributo.

- L'attributo ValidateCount è definito per il [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Come dichiarare le regole di convalida dell'Input](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Come dichiarare le regole di convalida dell'Input](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)