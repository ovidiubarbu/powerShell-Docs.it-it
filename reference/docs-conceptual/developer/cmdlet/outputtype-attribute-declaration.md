---
title: Dichiarazione dell'attributo OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365340"
---
# <a name="outputtype-attribute-declaration"></a>Dichiarazione dell'attributo OutputType

L'attributo `OutputType` identifica i tipi di .NET Framework restituiti da un cmdlet, una funzione o uno script.

## <a name="syntax"></a>Sintassi

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametri

È necessario digitare (`string[]` o `Type[]`). Specifica i tipi restituiti dalla funzione del cmdlet o dallo script.

ParameterSetName (String []) facoltativa. Specifica i set di parametri che restituiscono i tipi specificati nel parametro `type`.

providerCmdlet facoltativo. Specifica il cmdlet del provider che restituisce i tipi specificati nel parametro `type`.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
