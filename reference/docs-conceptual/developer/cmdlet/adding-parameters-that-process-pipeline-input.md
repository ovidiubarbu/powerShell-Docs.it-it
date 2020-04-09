---
title: Aggiunta di parametri che elaborano l'input della pipeline | Microsoft Docs
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
ms.openlocfilehash: 4966ac274713899e7ea9e0c375dca220a972a1b5
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978730"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Aggiunta di parametri che elaborano gli input della pipeline

Un'origine di input per un cmdlet è un oggetto nella pipeline che ha origine da un cmdlet upstream. Questa sezione descrive come aggiungere un parametro al cmdlet Get-proc, descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md), in modo che il cmdlet possa elaborare gli oggetti pipeline.

Questo cmdlet Get-proc usa un parametro `Name` che accetta l'input da un oggetto pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi forniti e quindi Visualizza le informazioni sui processi nella riga di comando.

## <a name="defining-the-cmdlet-class"></a>Definizione della classe cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet. Questo cmdlet recupera le informazioni sul processo, quindi il nome del verbo scelto qui è "Get". (Quasi tutti i tipi di cmdlet in grado di recuperare informazioni possono elaborare l'input della riga di comando). Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Di seguito è riportata la definizione di questo cmdlet Get-proc. I dettagli di questa definizione sono forniti durante [la creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definizione dell'input dalla pipeline

Questa sezione descrive come definire l'input dalla pipeline per un cmdlet. Questo cmdlet Get-proc definisce una proprietà che rappresenta il parametro `Name` come descritto in [aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md).
Per informazioni generali sulla dichiarazione dei parametri, vedere questo argomento.

Tuttavia, quando un cmdlet deve elaborare l'input della pipeline, i parametri devono essere associati ai valori di input dal runtime di Windows PowerShell. A tale scopo, è necessario aggiungere la parola chiave `ValueFromPipeline` o aggiungere la parola chiave `ValueFromPipelineByProperty` alla dichiarazione dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Specificare la parola chiave `ValueFromPipeline` se il cmdlet accede all'oggetto di input completo. Specificare il `ValueFromPipelineByProperty` se il cmdlet accede solo a una proprietà dell'oggetto.

Di seguito è illustrata la dichiarazione di parametro per il parametro `Name` di questo cmdlet Get-proc che accetta input della pipeline.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="35-44":::

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

La dichiarazione precedente imposta la parola chiave `ValueFromPipeline` su `true`, in modo che il runtime di Windows PowerShell associ il parametro all'oggetto in arrivo se l'oggetto è dello stesso tipo del parametro o se può essere assegnato allo stesso tipo. La parola chiave `ValueFromPipelineByPropertyName` viene inoltre impostata su `true`, in modo che il runtime di Windows PowerShell controllerà l'oggetto in ingresso per una proprietà `Name`. Se l'oggetto in ingresso ha tale proprietà, il runtime eseguirà il binding del parametro `Name` alla proprietà `Name` dell'oggetto in ingresso.

> [!NOTE]
> L'impostazione della parola chiave dell'attributo `ValueFromPipeline` per un parametro ha la precedenza sull'impostazione per la parola chiave `ValueFromPipelineByPropertyName`.

## <a name="overriding-an-input-processing-method"></a>Override di un metodo di elaborazione dell'input

Se il cmdlet prevede di gestire l'input della pipeline, è necessario eseguire l'override dei metodi di elaborazione dell'input appropriati. I metodi di elaborazione dell'input di base sono introdotti nella [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).

Questo cmdlet Get-proc esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) per gestire l'input del parametro `Name` fornito dall'utente o da uno script. Questo metodo otterrà i processi per ogni nome di processo richiesto o per tutti i processi se non viene specificato alcun nome. Si noti che all'interno di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)la chiamata a [WriteObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) è il meccanismo di output per l'invio di oggetti di output alla pipeline. Il secondo parametro di questa chiamata, `enumerateCollection`, viene impostato su `true` per indicare al runtime di Windows PowerShell di enumerare la matrice di oggetti processo e scrivere un processo alla volta nella riga di comando.

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

## <a name="code-sample"></a>Codice di esempio

Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET. Di conseguenza, un cmdlet può avere la necessità di definire un proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con Windows PowerShell, testarlo eseguendolo nella riga di comando. Ad esempio, testare il codice per il cmdlet di esempio. Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

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

- Immettere le righe seguenti per ottenere gli oggetti processo con una proprietà `Name` dai processi chiamati "IEXPLORE". Questo esempio usa il cmdlet `Get-Process` (fornito da Windows PowerShell) come comando upstream per recuperare i processi "IEXPLORE".

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  Viene visualizzato l'output seguente.

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))

[Riferimenti Windows PowerShell](../windows-powershell-reference.md)

[Esempi di cmdlet](./cmdlet-samples.md)
