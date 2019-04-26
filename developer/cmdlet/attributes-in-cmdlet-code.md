---
title: Gli attributi nel codice del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068684"
---
# <a name="attributes-in-cmdlet-code"></a>Attributi nel codice dei cmdlet

Per usare la funzionalità comune fornita da Windows PowerShell, le classi e proprietà pubbliche definite nel codice cmdlet sono decorate con attributi. Ad esempio, la definizione di classe seguente usa l'attributo Cmdlet per identificare la classe di Microsoft .NET Framework in cui il **Get-Proc** cmdlet viene implementato. (Questo cmdlet viene usato come esempio in questo documento ed è simile al `Get-Process` cmdlet forniti da Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Questi attributi vengono considerati i metadati perché l'implementazione è separata rispetto all'implementazione del codice di cmdlet. Quando il runtime di Windows PowerShell viene eseguito il cmdlet, riconosce gli attributi e quindi esegue l'azione appropriata per ogni attributo.

Anche se è possibile implementare la propria versione delle funzionalità fornite da questi attributi, una progettazione ottimale cmdlet Usa queste funzionalità comuni.

Per altre informazioni sugli attributi diversi che possono essere dichiarati in dei cmdlet, vedere [tipi di attributo](./attribute-types.md).

## <a name="see-also"></a>Vedere anche

[Tipi di attributo](./attribute-types.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
