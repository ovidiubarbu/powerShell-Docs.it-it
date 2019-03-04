---
title: Dichiarazione di proprietà come parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861377"
---
# <a name="declaring-properties-as-parameters"></a>Dichiarazione di proprietà come parametri

In questo argomento fornisce informazioni di base che è necessario comprendere prima di dichiarare i parametri di un cmdlet.

Per dichiarare i parametri di un cmdlet all'interno della classe cmdlet, definire le proprietà pubbliche che rappresentano ogni parametro e quindi aggiungere uno o più attributi di parametro per ogni proprietà. Il runtime di Windows PowerShell Usa gli attributi di parametro per identificare la proprietà come parametro del cmdlet. La sintassi di base per dichiarare l'attributo di parametro è `[Parameter()]`.

Di seguito è riportato un esempio di una proprietà definita come un parametro obbligatorio.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Ecco alcuni aspetti da ricordare riguardo a parametri.

- Un parametro deve essere esplicitamente contrassegnato come pubblico. Parametri non contrassegnati come pubblici impostati come interni e non verranno trovati dal runtime di Windows PowerShell.

- I parametri devono essere definiti come tipi di Microsoft .NET Framework per fornire una migliore convalida dei parametri. Ad esempio, i parametri che sono limitati a un valore all'esterno di un set di valori devono essere definiti come un tipo di enumerazione. I parametri che accettano un valore di Uniform Resource Identifier (URI) devono essere di tipo [System. URI](/dotnet/api/System.Uri).

- Evitare di parametri di base su stringhe per le proprietà tutto tranne testo libero.

- È possibile aggiungere un parametro a qualsiasi numero di set di parametri. Per altre informazioni sui set di parametri, vedere [imposta parametro di Cmdlet](./cmdlet-parameter-sets.md).

Windows PowerShell fornisce anche un set di parametri comuni che sono automaticamente disponibili per ogni cmdlet. Per altre informazioni su questi parametri e i relativi alias, vedere [parametri comuni del Cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Vedere anche

[Parametri comuni di cmdlet](./common-parameter-names.md)

[Tipi di parametro del Cmdlet](./types-of-cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
