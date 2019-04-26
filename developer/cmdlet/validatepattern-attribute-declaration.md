---
title: Dichiarazione di attributo ValidatePattern | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067128"
---
# <a name="validatepattern-attribute-declaration"></a>Dichiarazione dell'attributo ValidatePattern

L'attributo ValidatePattern consente di specificare un criterio di espressione regolare che convalida l'argomento di un parametro del cmdlet. Questo attributo può essere utilizzato anche dalle funzioni di Windows PowerShell.

Quando viene richiamato ValidatePattern all'interno di un cmdlet, il runtime di Windows PowerShell converte l'argomento del parametro di cmdlet in una stringa e quindi confronta tale stringa con il modello fornito dall'attributo ValidatePattern. Il cmdlet viene eseguito solo se la rappresentazione di stringa convertita dell'argomento e il modello fornito corrisponde. Se non corrispondono, viene generato un errore dal runtime di Windows PowerShell.

## <a name="syntax"></a>Sintassi

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parametri

`RegexString` ([System. String](/dotnet/api/System.String)) richiesto. Specifica un'espressione regolare che convalida l'argomento del parametro.

Opzioni ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) parametro denominato facoltativo. Specifica una combinazione bit per bit di [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flag che specificano opzioni di espressioni regolari.

## <a name="remarks"></a>Osservazioni

- Questo attributo può essere utilizzato una sola volta per ogni parametro.

- È possibile usare il `Option` parametro dell'attributo per definire ulteriormente il modello. Ad esempio, è possibile rendere il modello di maiuscole / minuscole.

- Se questo attributo viene applicato a una raccolta, ogni elemento della raccolta deve corrispondere al modello.

- L'attributo ValidatePattern è definito per il [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) classe.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
