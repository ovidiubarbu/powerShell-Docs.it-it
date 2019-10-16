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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365750"
---
# <a name="declaring-properties-as-parameters"></a>Dichiarazione di proprietà come parametri

In questo argomento vengono fornite informazioni di base che è necessario conoscere prima di dichiarare i parametri di un cmdlet.

Per dichiarare i parametri di un cmdlet all'interno della classe di cmdlet, definire le proprietà pubbliche che rappresentano ogni parametro, quindi aggiungere uno o più attributi di parametro a ogni proprietà. Il runtime di Windows PowerShell usa gli attributi dei parametri per identificare la proprietà come parametro del cmdlet. La sintassi di base per la dichiarazione dell'attributo Parameter è `[Parameter()]`.

Di seguito è riportato un esempio di una proprietà definita come parametro obbligatorio.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Ecco alcuni aspetti da ricordare sui parametri.

- Un parametro deve essere contrassegnato in modo esplicito come Public. I parametri che non sono contrassegnati come Public default come Internal e non verranno trovati dal runtime di Windows PowerShell.

- I parametri devono essere definiti come Microsoft .NET tipi di Framework per offrire una migliore convalida dei parametri. Ad esempio, i parametri limitati a un valore di un set di valori devono essere definiti come un tipo di enumerazione. I parametri che accettano un valore di Uniform Resource Identifier (URI) devono essere di tipo [System. Uri](/dotnet/api/System.Uri).

- Evitare i parametri di stringa di base per tutte le proprietà di testo in formato libero.

- È possibile aggiungere un parametro a un numero qualsiasi di set di parametri. Per ulteriori informazioni sui set di parametri, vedere [set di parametri del cmdlet](./cmdlet-parameter-sets.md).

Windows PowerShell fornisce anche un set di parametri comuni disponibili automaticamente per ogni cmdlet. Per altre informazioni su questi parametri e sui relativi alias, vedere [parametri comuni dei cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Vedere anche

[Parametri comuni cmdlet](./common-parameter-names.md)

[Tipi di parametro del cmdlet](./types-of-cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
