---
title: Come eseguire l'override dei metodi di elaborazione degli input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364470"
---
# <a name="how-to-override-input-processing-methods"></a>Come sostituire i metodi di elaborazione degli input

In questi esempi viene illustrato come sovrascrivere i metodi di elaborazione dell'input all'interno di un cmdlet. Questi metodi vengono usati per eseguire le operazioni seguenti:

- Il metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) viene usato per eseguire operazioni di avvio monouso valide per tutti gli oggetti elaborati dal cmdlet. Il runtime di Windows PowerShell chiama questo metodo una sola volta.

- Il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) viene utilizzato per elaborare gli oggetti passati al cmdlet. Il runtime di Windows PowerShell chiama questo metodo per ogni oggetto passato al cmdlet.

- Il metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) viene usato per eseguire operazioni di post-elaborazione monouso. Il runtime di Windows PowerShell chiama questo metodo una sola volta.

## <a name="to-override-the-beginprocessing-method"></a>Per eseguire l'override del metodo BeginProcessing

- Dichiarare un override protetto del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

La classe seguente stampa un messaggio di esempio. Per usare questa classe, modificare il verbo e il sostantivo nell'attributo cmdlet, modificare il nome della classe in modo che corrisponda al nuovo verbo e al sostantivo, quindi aggiungere la funzionalità richiesta all'override del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>Per eseguire l'override del metodo ProcessRecord

- Dichiarare un override protetto del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

La classe seguente stampa un messaggio di esempio. Per usare questa classe, modificare il verbo e il sostantivo nell'attributo cmdlet, modificare il nome della classe in modo che corrisponda al nuovo verbo e al sostantivo, quindi aggiungere la funzionalità richiesta all'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Per eseguire l'override del metodo EndProcessing

- Dichiarare un override protetto del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

La classe seguente stampa un esempio. Per usare questa classe, modificare il verbo e il sostantivo nell'attributo cmdlet, modificare il nome della classe in modo che corrisponda al nuovo verbo e al sostantivo, quindi aggiungere la funzionalità richiesta all'override del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
