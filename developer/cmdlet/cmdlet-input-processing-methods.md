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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794944"
---
# <a name="cmdlet-input-processing-methods"></a>Metodi di elaborazione degli input dei cmdlet

I cmdlet devono eseguire l'override di uno o più i metodi descritti in questo argomento per effettuare le operazioni di elaborazione dell'input. Questi metodi consentono al cmdlet di eseguire la pre-elaborazione operations, input operazioni di elaborazione e operazioni di post-elaborazione. Questi metodi consentono anche di arrestare l'elaborazione di cmdlet.

## <a name="pre-processing-tasks"></a>Attività di pre-elaborazione

I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodo per aggiungere eventuali operazioni di pre-elaborazione che sono valide per tutti i record che verranno elaborati in un secondo momento tramite il cmdlet. Quando Windows PowerShell elabora una pipeline di comandi, Windows PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline. Per altre informazioni sul modo in cui Windows PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Il codice seguente viene illustrata un'implementazione del [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) (metodo).

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Per un esempio più dettagliato di come usare il [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodo, vedere [esercitazione SelectStr](./selectstr-tutorial.md). In questa esercitazione, il **Select Str** cmdlet Usa il [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodo per generare l'espressione regolare che viene usato per cercare il record di elaborazione dell'input.

## <a name="input-processing-tasks"></a>Attività di elaborazione di input

I cmdlet possono eseguire l'override di [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metodo per elaborare l'input che viene inviato al cmdlet. Quando Windows PowerShell elabora una pipeline di comandi, Windows PowerShell chiama questo metodo per ogni record di input che viene elaborato dal cmdlet. Per altre informazioni sul modo in cui Windows PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Il codice seguente viene illustrata un'implementazione del [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (metodo).

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Per un esempio più dettagliato di come usare il [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metodo, vedere [esercitazione SelectStr](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Attività post-elaborazione

I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metodo per aggiungere tutte le operazioni post-elaborazione sono valide per tutti i record che sono stati elaborati dal cmdlet. Ad esempio, il cmdlet potrebbe essere necessario pulire le variabili oggetto dopo l'operazione è terminata l'elaborazione.

Quando Windows PowerShell elabora una pipeline di comandi, Windows PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline. Tuttavia, è importante ricordare che il runtime di Windows PowerShell non chiamerà il [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metodo se il cmdlet viene annullato metà attraverso l'elaborazione di input o se una terminazione errore si verifica in qualsiasi parte del cmdlet. Per questo motivo, un cmdlet che richiede la pulizia degli oggetti devono implementare l'intero [System. IDisposable](/dotnet/api/System.IDisposable) criterio, inclusi un finalizzatore, in modo che il runtime può chiamare entrambe le [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) metodi alla fine dell'elaborazione. Per altre informazioni sul modo in cui Windows PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Il codice seguente viene illustrata un'implementazione del [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (metodo).

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Per un esempio più dettagliato di come usare il [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metodo, vedere [esercitazione SelectStr](./selectstr-tutorial.md).

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
