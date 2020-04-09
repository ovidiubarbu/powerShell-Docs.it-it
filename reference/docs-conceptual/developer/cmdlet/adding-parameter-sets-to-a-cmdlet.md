---
title: Aggiunta di set di parametri a un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: 6e17ff3d8ad3f7b2c511b879c913633f320bf511
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978628"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Aggiunta dei set di parametri a un cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Informazioni importanti sui set di parametri

Windows PowerShell definisce un set di parametri come gruppo di parametri che operano insieme. Raggruppando i parametri di un cmdlet, è possibile creare un singolo cmdlet in grado di modificarne le funzionalità in base al gruppo di parametri specificato dall'utente.

Un esempio di cmdlet che usa due set di parametri per definire funzionalità diverse è il cmdlet `Get-EventLog` fornito da Windows PowerShell. Questo cmdlet restituisce informazioni diverse quando l'utente specifica il parametro `List` o `LogName`. Se viene specificato il parametro `LogName`, il cmdlet restituisce informazioni sugli eventi in un determinato registro eventi. Se viene specificato il parametro `List`, il cmdlet restituisce le informazioni sui file di log stessi (non le informazioni sull'evento che contengono). In questo caso, i parametri `List` e `LogName` identificano due set di parametri distinti.

Due aspetti importanti da ricordare per i set di parametri sono che il runtime di Windows PowerShell usa un solo set di parametri per un input specifico e che ogni set di parametri deve avere almeno un parametro univoco per il set di parametri.

Per illustrare l'ultimo punto, questo cmdlet Stop-proc usa tre set di parametri: `ProcessName`, `ProcessId`e `InputObject`. Ognuno di questi set di parametri ha un parametro che non si trova negli altri set di parametri. I set di parametri possono condividere altri parametri, ma il cmdlet usa i parametri univoci `ProcessName`, `ProcessId`e `InputObject` per identificare il set di parametri che deve essere usato dal runtime di Windows PowerShell.

## <a name="declaring-the-cmdlet-class"></a>Dichiarazione della classe cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet. Per questo cmdlet viene usato il verbo "Stop" del ciclo di vita perché il cmdlet interrompe i processi di sistema. Il nome del sostantivo "proc" viene usato perché il cmdlet funziona nei processi. Nella dichiarazione seguente si noti che il verbo del cmdlet e il nome del sostantivo sono riflessi nel nome della classe cmdlet.

> [!NOTE]
> Per ulteriori informazioni sui nomi dei verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Il codice seguente è la definizione di classe per questo cmdlet Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Dichiarazione dei parametri del cmdlet

Questo cmdlet definisce tre parametri necessari come input per il cmdlet (questi parametri definiscono anche i set di parametri), nonché un `Force` parametro che gestisce le operazioni del cmdlet e un parametro di `PassThru` che determina se il cmdlet invia un oggetto di output tramite la pipeline. Per impostazione predefinita, questo cmdlet non passa un oggetto tramite la pipeline. Per ulteriori informazioni su questi ultimi due parametri, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Dichiarazione del parametro Name

Questo parametro di input consente all'utente di specificare i nomi dei processi da arrestare. Si noti che la parola chiave dell'attributo `ParameterSetName` dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) specifica il set di parametri `ProcessName` per questo parametro.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs" range="44-58":::

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Si noti anche che l'alias "ProcessName" è assegnato a questo parametro.

### <a name="declaring-the-id-parameter"></a>Dichiarazione del parametro ID

Questo parametro di input consente all'utente di specificare gli identificatori dei processi da arrestare. Si noti che la parola chiave dell'attributo `ParameterSetName` dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) specifica il set di parametri `ProcessId`.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Si noti anche che l'alias "ProcessID" è assegnato a questo parametro.

### <a name="declaring-the-inputobject-parameter"></a>Dichiarazione del parametro InputObject

Questo parametro di input consente all'utente di specificare un oggetto di input che contiene informazioni sui processi da arrestare. Si noti che la parola chiave dell'attributo `ParameterSetName` dell'attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) specifica il set di parametri `InputObject` per questo parametro.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Si noti inoltre che questo parametro non ha alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Dichiarazione di parametri in più set di parametri

Sebbene sia necessario un parametro univoco per ogni set di parametri, i parametri possono appartenere a più di un set di parametri. In questi casi, assegnare al parametro Shared una dichiarazione di attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) per ogni set a cui appartiene il parametro. Se un parametro è presente in tutti i set di parametri, è necessario dichiarare l'attributo del parametro una sola volta e non è necessario specificare il nome del set di parametri.

## <a name="overriding-an-input-processing-method"></a>Override di un metodo di elaborazione dell'input

Ogni cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, più spesso questo sarà il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . In questo cmdlet viene eseguito l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) in modo che il cmdlet possa elaborare un numero qualsiasi di processi. Contiene un'istruzione SELECT che chiama un metodo diverso in base al set di parametri specificato dall'utente.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

I metodi di supporto chiamati dall'istruzione SELECT non sono descritti qui, ma è possibile visualizzarne l'implementazione nell'esempio di codice completo nella sezione successiva.

## <a name="code-sample"></a>Codice di esempio

Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample04](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET. Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con Windows PowerShell, testarlo eseguendolo nella riga di comando. Ecco alcuni test che illustrano come usare i parametri `ProcessId` e `InputObject` per testare i set di parametri per arrestare un processo.

- Con Windows PowerShell avviato, eseguire il cmdlet Stop-proc con il set di parametri `ProcessId` per arrestare un processo in base al relativo identificatore. In questo caso, il cmdlet usa il set di parametri `ProcessId` per arrestare il processo.

  ```
  PS> stop-proc -Id 444
  Confirm
  Are you sure you want to perform this action?
  Performing operation "stop-proc" on Target "notepad (444)".
  [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
  ```

- Con Windows PowerShell avviato, eseguire il cmdlet Stop-proc con il set di parametri `InputObject` per arrestare i processi nell'oggetto blocco note recuperato dal comando `Get-Process`.

  ```
  PS> get-process notepad | stop-proc
  Confirm
  Are you sure you want to perform this action?
  Performing operation "stop-proc" on Target "notepad (444)".
  [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
  ```

## <a name="see-also"></a>Vedere anche

[Creazione di un cmdlet che modifica il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Come creare un cmdlet di Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
