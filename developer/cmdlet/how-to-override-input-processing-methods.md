---
title: Come eseguire l'Override di metodi di elaborazione dell'Input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067944"
---
# <a name="how-to-override-input-processing-methods"></a>Come sostituire i metodi di elaborazione degli input

Questi esempi illustrano come sovrascrivere i metodi all'interno di un cmdlet di elaborazione dell'input. Questi metodi vengono usati per eseguire le operazioni seguenti:

- Il [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo viene utilizzato per eseguire operazioni di avvio occasionale che sono valide per tutti gli oggetti elaborati dal cmdlet. Il runtime di Windows PowerShell chiama questo metodo solo una volta.

- Il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo viene utilizzato per elaborare gli oggetti passati al cmdlet. Il runtime di Windows PowerShell chiama questo metodo per ogni oggetto passato al cmdlet.

- Il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo viene utilizzato per eseguire le operazioni di elaborazione post monouso. Il runtime di Windows PowerShell chiama questo metodo solo una volta.

## <a name="to-override-the-beginprocessing-method"></a>Per eseguire l'override del metodo BeginProcessing

- Dichiarare un override di protetto il [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (metodo).

La classe seguente viene stampato un messaggio di esempio. Per usare questa classe, modificare il verbo e sostantivo nell'attributo Cmdlet, modificare il nome della classe in modo da riflettere il nuovo verbo e sostantivo e quindi aggiungere le funzionalità richieste per l'override del [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (metodo).

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

- Dichiarare un override di protetto il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).

La classe seguente viene stampato un messaggio di esempio. Per usare questa classe, modificare il verbo e sostantivo nell'attributo Cmdlet, modificare il nome della classe in modo da riflettere il nuovo verbo e sostantivo e quindi aggiungere le funzionalità richieste per l'override del [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).

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

## <a name="to-override-the-endprocessing-method"></a>L'override del metodo EndProcessing

- Dichiarare un override di protetto il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo).

La classe seguente visualizza un esempio. Per usare questa classe, modificare il verbo e sostantivo nell'attributo Cmdlet, modificare il nome della classe in modo da riflettere il nuovo verbo e sostantivo e quindi aggiungere le funzionalità richieste per l'override del [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo).

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

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
