---
title: Tipi di attributi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364580"
---
# <a name="attribute-types"></a>Tipi di attributo

Gli attributi del cmdlet possono essere raggruppati in base alla funzionalità.
Le sezioni seguenti descrivono gli attributi disponibili e descrivono il funzionamento del runtime quando viene richiamato l'attributo.

## <a name="cmdlet-attributes"></a>Attributi dei cmdlet

### <a name="cmdlet"></a>Cmdlet

Identifica una classe .NET Framework come cmdlet.
Si tratta dell'attributo di base obbligatorio.
Per altre informazioni, vedere [dichiarazione dell'attributo del cmdlet](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Attributi parametro

### <a name="parameter"></a>Parametro

Identifica una proprietà pubblica nella classe del cmdlet come parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Specifica uno o più alias per un parametro.
Per altre informazioni, vedere [dichiarazione di attributo alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Attributi di convalida degli argomenti

### <a name="validatecount"></a>ValidateCount

Specifica il numero minimo e massimo di argomenti consentiti per un parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Specifica un numero minimo e massimo di caratteri per un argomento di parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Specifica un modello di espressione regolare a cui deve corrispondere l'argomento del parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Specifica i valori minimo e massimo per un argomento di parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Specifica un set di valori validi per l'argomento del parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
