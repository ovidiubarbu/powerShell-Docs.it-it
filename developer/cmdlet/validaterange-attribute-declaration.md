---
title: Dichiarazione di attributo ValidateRange | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067111"
---
# <a name="validaterange-attribute-declaration"></a>Dichiarazione dell'attributo ValidateRange

L'attributo ValidateRange specifica i valori minimi e massimo (intervallo) per l'argomento del parametro di cmdlet. Questo attributo può essere utilizzato anche dalle funzioni di Windows PowerShell.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parametri

`MinRange` ([System. Object](/dotnet/api/system.object)) richiesto. Specifica il valore minimo consentito.

`MaxRange` ([System. Object](/dotnet/api/system.object)) richiesto. Specifica il valore massimo consentito.

## <a name="remarks"></a>Osservazioni

- Il runtime di Windows PowerShell genera un errore di costruzione quando il valore della `MinRange` è maggiore del valore del parametro di `MaxRange` parametro.

- Il runtime di Windows PowerShell genera un errore di convalida nelle condizioni seguenti:

    - Quando il valore dell'argomento è inferiore al `MinRange` limite o maggiore di `MaxRange` limite.

    - Quando l'argomento non è dello stesso tipo di `MinRange` e il `MaxRange` parametri.

- L'attributo ValidateRange è definito per il [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) classe.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
