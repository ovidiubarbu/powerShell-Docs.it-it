---
title: Convalida Input parametro | Microsoft Docs
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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858847"
---
# <a name="validating-parameter-input"></a>Convalida degli input dei parametri

Windows PowerShell è possibile convalidare gli argomenti passati ai parametri del cmdlet in diversi modi. Windows PowerShell è possibile convalidare la lunghezza dell'intervallo e il modello di caratteri dell'argomento. È possibile convalidare il numero di argomenti disponibili (numero). Queste regole di convalida sono definite da attributi di convalida che vengono dichiarati con l'attributo di parametro nelle proprietà pubbliche della classe del cmdlet.

Per convalidare un argomento del parametro, il runtime di Windows PowerShell Usa le informazioni fornite dagli attributi di convalida per confermare che il valore del parametro prima di eseguita il cmdlet. Se l'input del parametro non è valido, l'utente riceve un messaggio di errore. Parametro ogni convalida definisce una regola di convalida applicato da Windows PowerShell.

Windows PowerShell consente di applicare le regole di convalida in base agli attributi seguenti.

ValidateCount specifica il numero minimo e massimo di argomenti che può accettare un parametro. Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).

ValidateLength specifica il numero minimo e massimo di caratteri nell'argomento del parametro. Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md).

ValidatePattern consente di specificare un'espressione regolare che convalida l'argomento del parametro. Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md).

ValidateRange specifica i valori minimi e massimo dell'argomento del parametro. Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).

ValidateSet specifica i valori validi per l'argomento del parametro. Per altre informazioni sulla sintassi usata per dichiarare questo attributo, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Come convalidare l'Input del parametro](./how-to-validate-parameter-input.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
