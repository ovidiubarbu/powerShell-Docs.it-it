---
title: Aggiunta di parametri che elaborano Pipeline Input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: def0ac2ff98575beb29c3c2a7d91a5a5c53e648e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854989"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Aggiunta di parametri che elaborano gli input della pipeline

Un'origine di input per un cmdlet è un oggetto nella pipeline proveniente da un cmdlet a monte. In questa sezione viene descritto come aggiungere un parametro al cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)) in modo che il cmdlet può elaborare gli oggetti pipeline.

Questo cmdlet Get-Process Usa un `Name` parametro che accetta l'input da un oggetto della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi specificati e quindi Visualizza le informazioni sui processi nella riga di comando.

## <a name="defining-the-cmdlet-class"></a>La definizione di classe del Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Questo cmdlet recupera le informazioni sul processo, in modo che il nome del verbo selezionato qui è "Get". (Quasi una sorta di cmdlet che è in grado di recuperare le informazioni può elaborare input della riga di comando). Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Di seguito è la definizione per il cmdlet Get-Process. Dettagli di questa definizione sono disponibili nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>La definizione di Input dalla Pipeline

In questa sezione viene descritto come definire l'input dalla pipeline per un cmdlet. Questo cmdlet Get-Proc definisce una proprietà che rappresenta il `Name` parametro, come descritto in [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md). (Vedere l'argomento per informazioni generali sulla dichiarazione di parametri).

Tuttavia, quando un cmdlet deve elaborare l'input della pipeline, deve avere i parametri associati a valori di input dal runtime di Windows PowerShell. A tale scopo, è necessario aggiungere il `ValueFromPipeline` parola chiave o aggiungere il `ValueFromPipelineByProperty` parola chiave per il [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione dell'attributo. Specificare il `ValueFromPipeline` parola chiave se il cmdlet accede all'oggetto di input completo. Specificare il `ValueFromPipelineByProperty` se il cmdlet accede solo una proprietà dell'oggetto.

Di seguito è riportata la dichiarazione di parametro per il `Name` parametro del cmdlet Get-Process che accetta l'input della pipeline.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

I set di dichiarazione precedente di `ValueFromPipeline` parola chiave da `true` in modo che il runtime di Windows PowerShell verrà associato il parametro all'oggetto in ingresso se l'oggetto è dello stesso tipo di parametro o se può essere assegnato lo stesso tipo. Il `ValueFromPipelineByPropertyName` parola chiave viene impostata su `true` in modo che il runtime di Windows PowerShell controllerà l'oggetto in ingresso per un `Name` proprietà. Se l'oggetto in ingresso ha una proprietà di questo tipo, il runtime verrà associato il `Name` parametro per il `Name` proprietà dell'oggetto in ingresso.

> [!NOTE]
> L'impostazione delle `ValueFromPipeline` parola chiave dell'attributo di un parametro ha la precedenza sull'impostazione del `ValueFromPipelineByPropertyName` (parola chiave).

## <a name="overriding-an-input-processing-method"></a>Si esegue l'override di un metodo di elaborazione dell'Input

Se il cmdlet deve gestire l'input della pipeline, è necessario eseguire l'override di metodi di elaborazione dell'input appropriati. In cui sono stati introdotti i metodi di elaborazione dell'input di base [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

Esegue l'override di questo cmdlet Get-Proc il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per gestire il `Name` input del parametro fornito dall'utente o uno script. Questo metodo otterranno i processi per ogni nome di processo richiesto o tutti i processi se viene fornito alcun nome. Si noti che nel [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la chiamata a [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) è riportato l'output meccanismo per l'invio di output oggetti alla pipeline. Il secondo parametro di questa chiamata `enumerateCollection`, è impostato su `true` indicare al runtime di Windows PowerShell per enumerare la matrice di oggetti processo e scrivere un solo processo alla volta nella riga di comando.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [esempio GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. Ad esempio, testare il codice per il cmdlet di esempio. Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Al prompt di Windows PowerShell, immettere i comandi seguenti per recuperare i nomi dei processi tramite la pipeline.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

Viene visualizzato l'output seguente.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Immettere le righe seguenti per ottenere gli oggetti processo che hanno un `Name` proprietà dai processi denominata "IEXPLORE". Questo esempio viene usato il `Get-Process` cmdlet (fornito da Windows PowerShell) come un comando per recuperare i processi "IEXPLORE" upstream.

    ```powershell
    PS> get-process iexplore | get-proc
    ```

Viene visualizzato l'output seguente.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri che elaborano gli Input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)

[Esempi di cmdlet](./cmdlet-samples.md)
