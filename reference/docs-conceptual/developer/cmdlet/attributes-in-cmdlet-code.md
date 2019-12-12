---
title: Attributi nel codice del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370000"
---
# <a name="attributes-in-cmdlet-code"></a>Attributi nel codice dei cmdlet

Per utilizzare la funzionalità comune fornita da Windows PowerShell, le classi e le proprietà pubbliche definite nel codice del cmdlet sono decorate con attributi. La definizione di classe seguente, ad esempio, usa l'attributo cmdlet per identificare la classe Microsoft .NET Framework in cui viene implementato il cmdlet **Get-proc** . Questo cmdlet viene usato come esempio in questo documento ed è simile al cmdlet `Get-Process` fornito da Windows PowerShell.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Questi attributi sono considerati metadati perché la loro implementazione è separata dall'implementazione del codice del cmdlet. Quando il runtime di Windows PowerShell esegue il cmdlet, riconosce gli attributi e quindi esegue l'azione appropriata per ogni attributo.

Sebbene sia necessario implementare una versione personalizzata della funzionalità fornita da questi attributi, una progettazione di cmdlet efficace utilizza queste funzionalità comuni.

Per ulteriori informazioni sui diversi attributi che possono essere dichiarati nei cmdlet, vedere [tipi](./attribute-types.md)di attributi.

## <a name="see-also"></a>Vedere anche

[Tipi di attributi](./attribute-types.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
