---
title: Dichiarazione dell'attributo ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369130"
---
# <a name="validaterange-attribute-declaration"></a>Dichiarazione dell'attributo ValidateRange

L'attributo ValidateRange specifica i valori minimo e massimo (intervallo) per l'argomento del parametro del cmdlet. Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametri

`MinRange` ([System. Object](/dotnet/api/system.object)) obbligatorio. Specifica il valore minimo consentito.

`MaxRange` ([System. Object](/dotnet/api/system.object)) obbligatorio. Specifica il valore massimo consentito.

## <a name="remarks"></a>Osservazioni

- Il runtime di Windows PowerShell genera un errore di costruzione quando il valore del parametro `MinRange` è maggiore del valore del parametro `MaxRange`.

- Il runtime di Windows PowerShell genera un errore di convalida nelle condizioni seguenti:

    - Quando il valore dell'argomento è minore del limite `MinRange` o maggiore del limite di `MaxRange`.

    - Quando l'argomento non è dello stesso tipo del `MinRange` e dei parametri di `MaxRange`.

- L'attributo ValidateRange è definito dalla classe [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
