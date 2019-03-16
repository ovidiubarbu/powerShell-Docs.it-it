---
title: Aggiunta del parametro imposta a un Cmdlet | Microsoft Docs
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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054986"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Aggiunta dei set di parametri a un cmdlet

In questa sezione viene descritto come aggiungere set di parametri al cmdlet Stop-Process (descritto nella [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)). Come per gli altri cmdlet Stop-Process descritto nella Guida per programmatori questo, questo cmdlet tenta di arrestare i processi che vengono recuperati usando il cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Gli argomenti in questa sezione includono quanto segue:

- [Informazioni utili sul set di parametri](#Adding-Parameter-Sets-to-a-Cmdlet)

- [La dichiarazione di classe del Cmdlet](#Declaring-the-Cmdlet-Class)

- [Dichiarando i parametri del Cmdlet](#Declaring-the-Parameters-of-the-Cmdlet)

- [Si esegue l'override di un metodo di elaborazione dell'Input](#Overriding-an-Input-Processing-Method)

- [Esempio di codice](#Declaring-the-Parameters-of-the-Cmdlet)

- [Definizione di tipi di oggetto e formattazione](#Defining-Object-Types-and-Formatting)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Informazioni utili sul set di parametri

Windows PowerShell consente di definire un set di parametri di un gruppo di parametri che vengono usati insieme. Raggruppando i parametri di un cmdlet, è possibile creare un singolo cmdlet che possono cambiare le funzionalità di base a quale gruppo di parametri specifica l'utente.

È un esempio di un cmdlet che usa due set di parametri per definire diverse funzionalità di `Get-EventLog` cmdlet fornito da Windows PowerShell. Questo cmdlet restituisce informazioni diverse, quando l'utente specifica i `List` o `LogName` parametro. Se il `LogName` parametro viene specificato, il cmdlet restituisce informazioni sugli eventi in un determinato registro eventi. Se il `List` parametro viene specificato, il cmdlet restituisce informazioni sul log di file (non le informazioni sull'evento contengono). In questo caso, il `List` e `LogName` parametro identificano due set di parametri separato.

Due aspetti importanti da ricordare riguardo a set di parametri è che il runtime di Windows PowerShell Usa un solo set di parametri per un input specifico e che ogni set di parametri deve contenere almeno un parametro che è univoco per il set di parametri.

Per illustrare questo ultimo punto, questo cmdlet Stop-Process Usa tre set di parametri: `ProcessName`, `ProcessId`, e `InputObject`. Ognuno di questi set di parametri contiene un parametro che non sia in altri set di parametri. I set di parametri è stato possibile condividere gli altri parametri, ma il cmdlet Usa i parametri univoci `ProcessName`, `ProcessId`, e `InputObject` per identificare quale set di parametri che deve usare il runtime di Windows PowerShell.

## <a name="declaring-the-cmdlet-class"></a>La dichiarazione di classe del Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Per questo cmdlet, viene utilizzato il verbo di ciclo di vita "Stop", perché il cmdlet arresta i processi di sistema. Il nome del sostantivo "Proc" viene usato perché il cmdlet può essere eseguita sui processi. Nella dichiarazione seguente, si noti che il nome del verbo e sostantivo cmdlet vengono riflesse nel nome di classe del cmdlet.

> [!NOTE]
> Per altre informazioni sui nomi dei verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Il codice seguente è la definizione di classe per questo cmdlet Stop-Process.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Dichiarando i parametri del Cmdlet

Questo cmdlet definisce tre parametri necessari come input al cmdlet (questi parametri anche definiscono i set di parametri), nonché una `Force` parametro che gestisce il cmdlet non e un `PassThru` parametro che determina se il cmdlet invia un oggetto di output tramite la pipeline. Per impostazione predefinita, questo cmdlet non passare un oggetto tramite la pipeline. Per altre informazioni su questi ultimi due parametri, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Dichiarare il parametro Name

Questo parametro input consente all'utente di specificare i nomi dei processi da arrestare. Si noti che il `ParameterSetName` parola chiave dell'attributo di [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo specifica il `ProcessName` di impostazione parametro per questo parametro.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

Si noti anche che l'alias "ProcessName" viene assegnato a questo parametro.

### <a name="declaring-the-id-parameter"></a>Dichiarare il parametro Id

Questo parametro input consente all'utente di specificare gli identificatori dei processi da arrestare. Si noti che il `ParameterSetName` parola chiave dell'attributo di [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo specifica il `ProcessId` set di parametri.

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

Si noti anche che l'alias "ProcessId" viene assegnato a questo parametro.

### <a name="declaring-the-inputobject-parameter"></a>Il parametro InputObject di dichiarazione

Questo parametro input consente all'utente di specificare un oggetto di input che contiene informazioni sui processi da arrestare. Si noti che il `ParameterSetName` parola chiave dell'attributo di [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo specifica il `InputObject` di impostazione parametro per questo parametro.

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

Si noti anche che questo parametro non ha alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Dichiarazione dei parametri in più set di parametri

Anche se è necessario un parametro univoco per ogni set di parametri, i parametri possono appartenere a più di un set di parametri. In questi casi, assegnare al parametro condiviso una [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione di attributo per ogni set a cui il parametro appartiene. Se un parametro in tutti i set di parametri, solo necessario dichiarare l'attributo parameter una sola volta e non è necessario specificare che il parametro del set di nome.

## <a name="overriding-an-input-processing-method"></a>Si esegue l'override di un metodo di elaborazione dell'Input

Ogni cmdlet è necessario eseguire l'override di un metodo di elaborazione dell'input, in genere si tratterà il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo). In questo cmdlet, il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) è sottoposto a override in modo che il cmdlet può elaborare qualsiasi numero di processi. Contiene un'istruzione Select che chiama un metodo diverso basato su quale set di parametri l'utente ha specificato.

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

I metodi Helper chiamati dall'istruzione Select non sono descritti di seguito, ma è possibile visualizzare la relativa implementazione nell'esempio di codice completo nella sezione successiva.

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [esempio StopProcessSample04](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .NET. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. Ecco alcuni test che illustrano come il `ProcessId` e `InputObject` parametri possono essere utilizzati per i set di parametri per arrestare un processo di test.

- Con Windows PowerShell avviata, eseguire il cmdlet Stop-Process con il `ProcessId` parametro impostato su arrestare un processo in base al relativo identificatore. In questo caso, Usa il cmdlet di `ProcessId` parametro impostato per arrestare il processo.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Con Windows PowerShell avviata, eseguire il cmdlet Stop-Process con il `InputObject` parametro è impostato per arrestare i processi per l'oggetto di blocco note recuperato tramite il `Get-Process` comando.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Vedere anche

[Creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Come creare un Cmdlet di Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
