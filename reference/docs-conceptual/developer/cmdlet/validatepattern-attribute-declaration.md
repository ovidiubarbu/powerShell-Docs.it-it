---
title: Dichiarazione dell'attributo ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369160"
---
# <a name="validatepattern-attribute-declaration"></a>Dichiarazione dell'attributo ValidatePattern

L'attributo ValidatePattern specifica un modello di espressione regolare che convalida l'argomento di un parametro del cmdlet. Questo attributo può essere usato anche dalle funzioni di Windows PowerShell.

Quando ValidatePattern viene richiamato all'interno di un cmdlet, il runtime di Windows PowerShell converte l'argomento del parametro del cmdlet in una stringa e quindi confronta tale stringa con il modello fornito dall'attributo ValidatePattern. Il cmdlet viene eseguito solo se la rappresentazione di stringa convertita dell'argomento e il criterio fornito corrispondono. Se non corrispondono, viene generato un errore dal runtime di Windows PowerShell.

## <a name="syntax"></a>Sintassi

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parametri

`RegexString` ([System. String](/dotnet/api/System.String)) obbligatorio. Specifica un'espressione regolare che convalida l'argomento del parametro.

Options ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) parametro denominato facoltativo. Specifica una combinazione bit per bit di flag [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) che specificano le opzioni di espressione regolare.

## <a name="remarks"></a>Osservazioni

- Questo attributo può essere utilizzato una sola volta per ogni parametro.

- Per definire ulteriormente il modello, è possibile usare il parametro `Option` dell'attributo. Ad esempio, è possibile rendere la distinzione tra maiuscole e minuscole.

- Se questo attributo viene applicato a una raccolta, ogni elemento nella raccolta deve corrispondere al modello.

- L'attributo ValidatePattern è definito dalla classe [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
