---
title: Creazione di un Cmdlet senza parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860647"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Creazione di un cmdlet senza parametri

In questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni per la pipeline. I cmdlet descritti di seguito è un cmdlet Get-Process che recupera le informazioni sui processi del computer locale e quindi Visualizza le informazioni nella riga di comando.

Gli argomenti in questa sezione includono quanto segue:

- [Il Cmdlet di denominazione](#Naming-the-Cmdlet)

- [La definizione di classe del Cmdlet](#Defining-the-Cmdlet-Class)

- [Si esegue l'override di un metodo di elaborazione dell'Input](#Overriding-an-Input-Processing-Method)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#Defining-Object-Types-and-Formatting)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

> [!NOTE]
> Tenere presente che, durante la scrittura di cmdlet, gli assembly di riferimento Windows PowerShell® vengono scaricati nel disco (per impostazione predefinita a C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Non sono installati nella Global Assembly Cache (GAC).

## <a name="naming-the-cmdlet"></a>Il Cmdlet di denominazione

Nome di un cmdlet è costituito da un verbo indicante che l'azione intrapresa dal cmdlet e un nome che indica gli elementi che interviene il cmdlet. Poiché il cmdlet Get-Process di esempio recupera gli oggetti processo, utilizza il verbo "Get", definiti dal [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumerazione e il sostantivo "Proc" per indicare che il cmdlet elabora gli elementi di processo.

La denominazione dei cmdlet, non usare uno qualsiasi dei seguenti caratteri: #, () {} [] & - / \ $;: "' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Scelta di un sostantivo

È consigliabile scegliere un sostantivo specifico. È consigliabile usare un sostantivo singolare preceduto da una versione abbreviata del nome del prodotto. Un nome di cmdlet di esempio di questo tipo è "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Scelta di un verbo

È consigliabile usare un verbo dal set di nomi di verbi approvati di cmdlet. Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>La definizione di classe del Cmdlet

Dopo aver scelto un nome di cmdlet, definire una classe .NET per implementare il cmdlet. Ecco la definizione di classe per questo cmdlet Get-Process di esempio:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Si noti che precede la definizione della classe, il [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributo, con la sintassi `[Cmdlet(verb, noun, ...)]`, viene usato per identificare questa classe come un cmdlet. Questo è l'unico attributo obbligatorio per tutti i cmdlet, e consente al runtime di Windows PowerShell di chiamarle in modo corretto. È possibile impostare le parole chiave di attributo per un'ulteriore dichiarare la classe se necessario. Tenere presente che la dichiarazione di attributo per la nostra classe GetProcCommand esempio dichiara solo i nomi di verbo e sostantivo per il cmdlet Get-Process.

> [!NOTE]
> Per tutte le classi di attributo di Windows PowerShell, le parole chiave che è possibile impostare corrispondono alle proprietà della classe di attributo.

Quando si rinomina la classe del cmdlet, è buona norma in modo da riflettere il nome del cmdlet nel nome della classe. A tale scopo, usare il modulo "VerbNounCommand" e sostituire "Verbo" e "Nome" con il verbo e sostantivo utilizzato per il nome del cmdlet. Come illustrato nella definizione di classe precedenti, il cmdlet Get-Process di esempio definisce una classe denominata GetProcCommand, che deriva dal [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe di base.

> [!IMPORTANT]
> Se si desidera definire un cmdlet che accede direttamente al runtime di Windows PowerShell, la classe .NET debba derivare dal [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe di base. Per altre informazioni su questa classe, vedere [creazione di un Cmdlet di tale set di parametri definisce](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> La classe per un cmdlet deve essere esplicitamente contrassegnata come pubblica. Le classi che non siano contrassegnate come pubblici per impostazione predefinita saranno interno e non verranno trovate dal runtime di Windows PowerShell.

Windows PowerShell Usa il [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) dello spazio dei nomi per le relative classi di cmdlet. È consigliabile inserire le classi di cmdlet in uno spazio dei nomi di comandi dello spazio dei nomi API, ad esempio, xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Si esegue l'override di un metodo di elaborazione dell'Input

Il [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornisce tre metodi di elaborazione di input principale, almeno uno dei quali è necessario eseguire l'override del cmdlet. Per altre informazioni sul modo in cui Windows PowerShell elabora i record, vedere [modalità di funzionamento di Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Per tutti i tipi di input, il runtime di Windows PowerShell viene chiamato [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) per abilitare l'elaborazione. Se il cmdlet deve eseguire alcune pre-elaborazione o il programma di installazione, è possibile eseguire questa operazione eseguendo l'override di questo metodo.

> [!NOTE]
> Windows PowerShell Usa il termine "record" per descrivere il set di valori di parametro fornito quando viene chiamato un cmdlet.

Se il cmdlet accetta l'input della pipeline, è necessario eseguire l'override di [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo e facoltativamente il [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)metodo. Ad esempio, un cmdlet potrebbe sostituire entrambi i metodi se raccoglie tutti i di input usando [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e quindi agisce sull'input come un intero anziché come un elemento alla volta, come il `Sort-Object` cmdlet non.

Se il cmdlet non accetta input della pipeline, è necessario eseguire l'override di [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo). Tenere presente che questo metodo viene spesso utilizzato al posto di [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando il cmdlet non può funzionare con un elemento alla volta, come avviene per un cmdlet di ordinamento.

Poiché il cmdlet Get-Process di esempio deve ricevere l'input della pipeline, viene eseguito l'override di [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo e utilizza le implementazioni predefinite per [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Il [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) sostituzione consente di recuperare i processi e li scrive in riga di comando tramite il [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metodo.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Aspetti da ricordare riguardo l'elaborazione dell'Input

- L'origine predefinita per l'input è un oggetto esplicito (ad esempio, una stringa) fornito dall'utente nella riga di comando. Per altre informazioni, vedere [creazione di un Cmdlet per l'Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md).

- Un metodo di elaborazione dell'input possono anche ricevere input dall'oggetto di output di un cmdlet upstream nella pipeline. Per altre informazioni, vedere [creazione di un Cmdlet per l'Input del processo della Pipeline](./adding-parameters-that-process-pipeline-input.md). Tenere presente che il cmdlet può ricevere input da una combinazione della riga di comando e la pipeline di origini.

- Il cmdlet a valle potrebbe non restituire a lungo o non ereditarli affatto. Per questo motivo, l'input l'elaborazione del metodo nel cmdlet non consigliabile mantenere i blocchi durante le chiamate a [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), in particolare i blocchi per il quale l'ambito si estende oltre l'istanza del cmdlet.

> [!IMPORTANT]
> I cmdlet non devono mai chiamare [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) o l'equivalente.

- Il cmdlet potrebbe essere variabili di oggetto per pulire al termine l'elaborazione (ad esempio, se si apre un handle di file nel [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (metodo) e mantiene l'handle per l'uso aprendo [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). È importante ricordare che il runtime di Windows PowerShell non chiama sempre il [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo, che deve eseguire la pulizia degli oggetti.

Ad esempio, [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) non può essere chiamato se il cmdlet viene annullato punto intermedio o se una terminazione errore si verifica in qualsiasi parte del cmdlet. Pertanto, un cmdlet che richiede la pulizia degli oggetti devono implementare l'intero [System. IDisposable](/dotnet/api/System.IDisposable) criterio, inclusi il finalizzatore, in modo che il runtime può chiamare sia [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) alla fine dell'elaborazione.

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [esempio GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .NET. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. Il codice per il cmdlet Get-Process di esempio è piccolo, ma viene ancora utilizzato il runtime di Windows PowerShell e un oggetto di .NET esistente, è sufficiente per essere efficiente. È possibile testarlo per comprendere meglio ciò che è possibile eseguire Get-Process e come è possibile usare il proprio output. Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Avviare Windows PowerShell e ottenere i processi correnti in esecuzione nel computer.

    ```powershell
    get-proc
    ```

    Viene visualizzato l'output seguente.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Assegnare una variabile ai risultati del cmdlet per semplificarne la manipolazione.

    ```powershell
    $p=get-proc
    ```

3. Ottiene il numero di processi.

    ```powershell
    $p.length
    ```

    Viene visualizzato l'output seguente.

    ```output
    63
    ```

4. Recuperare un processo specifico.

    ```powershell
    $p[6]
    ```

    Viene visualizzato l'output seguente.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Ottenere l'ora di inizio di questo processo.

    ```powershell
    $p[6].starttime
    ```

    Viene visualizzato l'output seguente.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Ottenere i processi per cui il numero di handle è maggiore di 500 e ordinare il risultato.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Viene visualizzato l'output seguente.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Usare il `Get-Member` cmdlet per elencare le proprietà disponibili per ogni processo.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Viene visualizzato l'output seguente.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Vedere anche

[Creazione di un Cmdlet per elaborare l'Input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Creazione di un Cmdlet per elaborare l'Input della Pipeline](./adding-parameters-that-process-pipeline-input.md)

[Come creare un Cmdlet di Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estensione di tipi di oggetto e la formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Funzionamento di Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)

[Esempi di cmdlet](./cmdlet-samples.md)