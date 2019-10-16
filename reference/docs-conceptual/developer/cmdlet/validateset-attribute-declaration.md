---
title: Dichiarazione dell'attributo ValidateSet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364280"
---
# <a name="validateset-attribute-declaration"></a>Dichiarazione dell'attributo ValidateSet

L'attributo ValidateSetAttribute specifica un set di valori possibili per un argomento di parametro del cmdlet. Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.

Quando si specifica questo attributo, il runtime di Windows PowerShell determina se l'argomento fornito per il parametro del cmdlet corrisponde a un elemento nel set di elementi fornito. Il cmdlet viene eseguito solo se l'argomento del parametro corrisponde a un elemento nel set. Se non viene trovata alcuna corrispondenza, il runtime di Windows PowerShell genera un errore.

## <a name="syntax"></a>Sintassi

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parametri

`ValidValues` ([System. String](/dotnet/api/System.String)) obbligatorio. Specifica i valori validi per gli elementi di parametro. Nell'esempio seguente viene illustrato come specificare un elemento o più elementi.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) parametro denominato facoltativo. Il valore predefinito di `true` indica che la distinzione tra maiuscole e minuscole viene ignorata. Il valore `false` rende il cmdlet con distinzione tra maiuscole e minuscole.

## <a name="remarks"></a>Osservazioni

- Questo attributo può essere utilizzato una sola volta per ogni parametro.

- Se il valore del parametro è una matrice, ogni elemento della matrice deve corrispondere a un elemento del set di attributi.

- L'attributo ValidateSetAttribute è definito dalla classe [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
