---
title: I metodi di elaborazione dell'Input cmdlet | Microsoft Docs
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
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670316"
---
# <a name="cmdlet-input-processing-methods"></a>Metodi di elaborazione degli input dei cmdlet

I cmdlet devono eseguire l'override di uno o più i metodi descritti in questo argomento per effettuare le operazioni di elaborazione dell'input.
Questi metodi consentono al cmdlet di eseguire le operazioni di pre-elaborazione, l'elaborazione dell'input e post-elaborazione.
Questi metodi consentono anche di arrestare l'elaborazione di cmdlet.
Per un esempio più dettagliato di come usare questi metodi, vedere [SelectStr esercitazione](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Operazioni di pre-elaborazione

I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo per aggiungere eventuali operazioni di pre-elaborazione che sono valide per tutti i record che verranno elaborati in un secondo momento tramite il cmdlet.
Quando PowerShell elabora una pipeline di comandi, PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline.
Per altre informazioni sul modo in cui PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](/previous-versions/ms714429(v=vs.85)).

Il codice seguente viene illustrata un'implementazione del metodo BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Operazioni di elaborazione dell'input

I cmdlet possono eseguire l'override di [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per elaborare l'input che viene inviato al cmdlet.
Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo per ogni record di input che viene elaborato dal cmdlet.
Per altre informazioni sul modo in cui PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](/previous-versions/ms714429(v=vs.85)).

Il codice seguente viene illustrata un'implementazione del metodo ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Operazioni di post-elaborazione

I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo per aggiungere tutte le operazioni post-elaborazione sono valide per tutti i record che sono stati elaborati dal cmdlet.
Ad esempio, il cmdlet potrebbe essere necessario pulire le variabili oggetto dopo l'operazione è terminata l'elaborazione.

Quando PowerShell elabora una pipeline di comandi, PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline.
Tuttavia, è importante ricordare che il runtime di PowerShell non chiamerà il metodo EndProcessing se il cmdlet viene annullato metà attraverso l'elaborazione di input o se si verifica un errore irreversibile in qualsiasi parte del cmdlet.
Per questo motivo, un cmdlet che richiede la pulizia degli oggetti devono implementare l'intero [System. IDisposable](/dotnet/api/System.IDisposable) criterio, inclusi un finalizzatore, in modo che il runtime può chiamare entrambe le EndProcessing e [ IDisposable](/dotnet/api/System.IDisposable.Dispose) metodi alla fine dell'elaborazione.
Per altre informazioni sul modo in cui PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](/previous-versions/ms714429(v=vs.85)).

Il codice seguente viene illustrata un'implementazione del metodo EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr Tutorial](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
