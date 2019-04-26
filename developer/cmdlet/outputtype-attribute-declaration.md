---
title: Dichiarazione di attributo OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067604"
---
# <a name="outputtype-attribute-declaration"></a>Dichiarazione dell'attributo OutputType

Il `OutputType` attributo identifica i tipi di .NET Framework restituiti da un cmdlet, funzione o script.

## <a name="syntax"></a>Sintassi

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametri

Tipo (`string[]` o `Type[]`) richiesto. Specifica i tipi restituiti dalla funzione di cmdlet o script.

ParameterSetName (string[]) facoltativo. Specifica il set di parametri che restituiscono i tipi specificati nel `type` parametro.

providerCmdlet facoltativo. Specifica i cmdlet del provider che restituisce i tipi specificati nel `type` parametro.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
