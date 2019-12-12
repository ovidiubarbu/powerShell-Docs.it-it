---
title: Metodi di elaborazione degli input dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369870"
---
# <a name="cmdlet-input-processing-methods"></a>Metodi di elaborazione degli input dei cmdlet

I cmdlet devono eseguire l'override di uno o più metodi di elaborazione dell'input descritti in questo argomento per eseguire il lavoro.
Questi metodi consentono al cmdlet di eseguire operazioni di pre-elaborazione, elaborazione dell'input e post-elaborazione.
Questi metodi consentono inoltre di arrestare l'elaborazione dei cmdlet.
Per un esempio più dettagliato di come usare questi metodi, vedere [esercitazione su SelectStr](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Operazioni di pre-elaborazione

I cmdlet devono eseguire l'override del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) per aggiungere tutte le operazioni di pre-elaborazione valide per tutti i record che verranno elaborati successivamente dal cmdlet.
Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo una volta per ogni istanza del cmdlet nella pipeline.
Per altre informazioni su come PowerShell richiama la pipeline di comandi, vedere [ciclo](/previous-versions/ms714429(v=vs.85))di vita dell'elaborazione dei cmdlet.

Nel codice seguente viene illustrata un'implementazione del metodo BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Operazioni di elaborazione dell'input

I cmdlet possono eseguire l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) per elaborare l'input inviato al cmdlet.
Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo per ogni record di input elaborato dal cmdlet.
Per altre informazioni su come PowerShell richiama la pipeline di comandi, vedere [ciclo](/previous-versions/ms714429(v=vs.85))di vita dell'elaborazione dei cmdlet.

Nel codice seguente viene illustrata un'implementazione del metodo ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Operazioni di post-elaborazione

I cmdlet devono eseguire l'override del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) per aggiungere eventuali operazioni di post-elaborazione valide per tutti i record elaborati dal cmdlet.
Ad esempio, il cmdlet potrebbe dover pulire le variabili oggetto dopo che è stata completata l'elaborazione.

Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo una volta per ogni istanza del cmdlet nella pipeline.
Tuttavia, è importante ricordare che il runtime di PowerShell non chiamerà il metodo EndProcessing se il cmdlet viene annullato a metà durante l'elaborazione dell'input o se si verifica un errore di terminazione in qualsiasi parte del cmdlet.
Per questo motivo, un cmdlet che richiede la pulizia degli oggetti deve implementare il modello [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluso un finalizzatore, in modo che il runtime possa chiamare i metodi EndProcessing e [System. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) alla fine dell'elaborazione.
Per altre informazioni su come PowerShell richiama la pipeline di comandi, vedere [ciclo](/previous-versions/ms714429(v=vs.85))di vita dell'elaborazione dei cmdlet.

Nel codice seguente viene illustrata un'implementazione del metodo EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Esercitazione su SelectStr](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
