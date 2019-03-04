---
title: Tipi di attributo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863807"
---
# <a name="attribute-types"></a>Tipi di attributo

Gli attributi di cmdlet possono essere raggruppati per funzionalità.
Le sezioni seguenti descrivono gli attributi disponibili e descrivono l'azione di runtime quando viene richiamato l'attributo.

## <a name="cmdlet-attributes"></a>Attributi dei cmdlet

### <a name="cmdlet"></a>Cmdlet

Identifica una classe .NET Framework come un cmdlet.
Si tratta dell'attributo di base obbligatorio.
Per altre informazioni, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Attributi dei parametri

### <a name="parameter"></a>Parametro

Identifica una proprietà pubblica della classe cmdlet come un parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Specifica uno o più alias per un parametro.
Per altre informazioni, vedere [dichiarazione di attributo Alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Attributi di convalida di argomenti

### <a name="validatecount"></a>ValidateCount

Specifica il numero minimo e massimo di argomenti che sono consentite per un parametro del cmdlet.
Per altre informazioni, vedere [dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Specifica un numero minimo e massimo di caratteri per un argomento del cmdlet di parametro.
Per altre informazioni, vedere [dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Specifica un criterio di espressione regolare che deve corrispondere l'argomento del parametro di cmdlet.
Per altre informazioni, vedere [dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Specifica i valori minimi e massimo per un argomento del cmdlet di parametro.
Per altre informazioni, vedere [dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Specifica un set di valori validi per l'argomento del parametro di cmdlet.
Per altre informazioni, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
