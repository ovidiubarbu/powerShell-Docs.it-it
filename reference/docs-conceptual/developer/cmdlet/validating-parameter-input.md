---
title: Convalida input parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363510"
---
# <a name="validating-parameter-input"></a>Convalida degli input dei parametri

PowerShell può convalidare gli argomenti passati ai parametri dei cmdlet in diversi modi.
PowerShell può convalidare la lunghezza, l'intervallo e il modello dei caratteri dell'argomento.
Può convalidare il numero di argomenti disponibili (conteggio).
Queste regole di convalida sono definite dagli attributi di convalida dichiarati con l'attributo Parameter sulle proprietà pubbliche della classe cmdlet.

Per convalidare un argomento di parametro, il runtime di PowerShell usa le informazioni fornite dagli attributi di convalida per confermare il valore del parametro prima dell'esecuzione del cmdlet.
Se l'input del parametro non è valido, l'utente riceve un messaggio di errore.
Ogni parametro di convalida definisce una regola di convalida che viene applicata da PowerShell.

PowerShell applica le regole di convalida in base ai seguenti attributi.

### <a name="validatecount"></a>ValidateCount

Specifica il numero minimo e massimo di argomenti che un parametro può accettare.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Specifica il numero minimo e massimo di caratteri nell'argomento del parametro.
Per altre informazioni, vedere [dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Specifica un'espressione regolare che convalida l'argomento del parametro.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Specifica i valori minimo e massimo dell'argomento del parametro.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Specifica i valori validi per l'argomento del parametro.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Come convalidare l'input del parametro](./how-to-validate-parameter-input.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
