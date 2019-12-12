---
title: Creazione di un cmdlet senza parametri | Microsoft Docs
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
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415663"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Creazione di un cmdlet senza parametri

In questa sezione viene descritto come creare un cmdlet che recupera le informazioni dal computer locale senza l'utilizzo di parametri e quindi scrive le informazioni nella pipeline. Il cmdlet descritto di seguito è un cmdlet Get-proc che recupera le informazioni sui processi del computer locale e quindi visualizza tali informazioni nella riga di comando.

> [!NOTE]
> Tenere presente che quando si scrivono i cmdlet, gli assembly di riferimento® di Windows PowerShell vengono scaricati su disco (per impostazione predefinita, in C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Non sono installati nella global assembly cache (GAC).

## <a name="naming-the-cmdlet"></a>Assegnazione di un nome al cmdlet

Il nome di un cmdlet è costituito da un verbo che indica l'azione eseguita dal cmdlet e da un sostantivo che indica gli elementi su cui agisce il cmdlet. Poiché questo cmdlet Get-proc di esempio recupera gli oggetti processo, usa il verbo "Get", definito dall'enumerazione [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) e il sostantivo "proc" per indicare che il cmdlet funziona sugli elementi del processo.

Quando si assegnano nomi ai cmdlet, non usare i caratteri seguenti: #, () {} [] &-/\ $; : "' < > &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Scelta di un sostantivo

È necessario scegliere un sostantivo specifico. È preferibile usare un sostantivo singolare preceduto da una versione abbreviata del nome del prodotto. Un esempio di nome di cmdlet di questo tipo è "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Scelta di un verbo

È necessario usare un verbo dal set di nomi di verbi di cmdlet approvati. Per ulteriori informazioni sui verbi dei cmdlet approvati, vedere [nomi dei verbi dei cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definizione della classe cmdlet

Una volta scelto il nome di un cmdlet, definire una classe .NET per implementare il cmdlet. Di seguito è illustrata la definizione di classe per questo cmdlet Get-proc di esempio:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Si noti che precedente alla definizione della classe, l'attributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , con la sintassi `[Cmdlet(verb, noun, ...)]`, viene usato per identificare questa classe come un cmdlet. Questo è l'unico attributo obbligatorio per tutti i cmdlet e consente al runtime di Windows PowerShell di chiamarli correttamente. È possibile impostare le parole chiave degli attributi per dichiarare ulteriormente la classe se necessario. Tenere presente che la dichiarazione di attributo per la classe GetProcCommand di esempio dichiara solo i nomi dei sostantivi e dei verbi per il cmdlet Get-proc.

> [!NOTE]
> Per tutte le classi di attributi di Windows PowerShell, le parole chiave che è possibile impostare corrispondono alle proprietà della classe Attribute.

Quando si denomina la classe del cmdlet, è consigliabile riflettere il nome del cmdlet nel nome della classe. A tale scopo, utilizzare il formato "VerbNounCommand" e sostituire "verb" e "noun" con il verbo e il sostantivo utilizzati nel nome del cmdlet. Come illustrato nella definizione di classe precedente, il cmdlet Get-proc di esempio definisce una classe denominata GetProcCommand, che deriva dalla classe di base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .

> [!IMPORTANT]
> Se si vuole definire un cmdlet che accede direttamente al runtime di Windows PowerShell, la classe .NET deve derivare dalla classe di base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Per ulteriori informazioni su questa classe, vedere [creazione di un cmdlet che definisce i set di parametri](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> La classe per un cmdlet deve essere contrassegnata in modo esplicito come Public. Per impostazione predefinita, le classi non contrassegnate come pubbliche saranno interne e non verranno trovate dal runtime di Windows PowerShell.

Windows PowerShell usa lo spazio dei nomi [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) per le classi di cmdlet. Si consiglia di inserire le classi di cmdlet in uno spazio dei nomi Commands dello spazio dei nomi dell'API, ad esempio, xxx. PS. Commands.

## <a name="overriding-an-input-processing-method"></a>Override di un metodo di elaborazione dell'input

La classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) fornisce tre metodi principali di elaborazione dell'input, almeno uno dei quali deve eseguire l'override del cmdlet. Per ulteriori informazioni sul modo in cui Windows PowerShell elabora i record, vedere funzionamento di [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

Per tutti i tipi di input, il runtime di Windows PowerShell chiama [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) per abilitare l'elaborazione. Se il cmdlet deve eseguire una pre-elaborazione o un programma di installazione, è possibile eseguire questa operazione eseguendo l'override di questo metodo.

> [!NOTE]
> Windows PowerShell usa il termine "record" per descrivere il set di valori di parametro fornito quando viene chiamato un cmdlet.

Se il cmdlet accetta input della pipeline, deve eseguire l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e, facoltativamente, del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Ad esempio, un cmdlet potrebbe eseguire l'override di entrambi i metodi se raccoglie tutti gli input usando [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e quindi opera sull'input nel suo complesso anziché su un elemento alla volta, come fa il cmdlet `Sort-Object`.

Se il cmdlet non accetta input della pipeline, deve eseguire l'override del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Tenere presente che questo metodo viene spesso usato al posto di [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando il cmdlet non può funzionare su un elemento alla volta, come nel caso di un cmdlet di ordinamento.

Poiché questo cmdlet Get-proc di esempio deve ricevere input della pipeline, esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e usa le implementazioni predefinite per [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). L'override di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) recupera i processi e li scrive nella riga di comando usando il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

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

#### <a name="things-to-remember-about-input-processing"></a>Aspetti da ricordare sull'elaborazione dell'input

- L'origine predefinita per l'input è un oggetto esplicito, ad esempio una stringa, fornito dall'utente nella riga di comando. Per ulteriori informazioni, vedere [creazione di un cmdlet per elaborare l'input della riga di comando](./adding-parameters-that-process-command-line-input.md).

- Un metodo di elaborazione dell'input può anche ricevere input dall'oggetto di output di un cmdlet upstream sulla pipeline. Per ulteriori informazioni, vedere [creazione di un cmdlet per elaborare l'input della pipeline](./adding-parameters-that-process-pipeline-input.md). Tenere presente che il cmdlet può ricevere input da una combinazione di origini della riga di comando e di pipeline.

- È possibile che il cmdlet downstream non venga restituito per molto tempo. Per questo motivo, il metodo di elaborazione dell'input nel cmdlet non deve mantenere i blocchi durante le chiamate a [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), in particolare i blocchi per i quali l'ambito si estende oltre l'istanza del cmdlet.

> [!IMPORTANT]
> I cmdlet non devono mai chiamare [System. Console. WriteLine *](/dotnet/api/System.Console.WriteLine) o l'equivalente.

- Il cmdlet potrebbe avere variabili oggetto da pulire al termine dell'elaborazione, ad esempio se apre un handle di file nel metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e mantiene l'handle aperto per l'uso da parte di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). È importante ricordare che il runtime di Windows PowerShell non chiama sempre il metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , che deve eseguire la pulizia degli oggetti.

Ad esempio, [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) potrebbe non essere chiamato se il cmdlet viene annullato a metà o se si verifica un errore di terminazione in qualsiasi parte del cmdlet. Pertanto, un cmdlet che richiede la pulizia degli oggetti deve implementare il modello [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluso il finalizzatore, in modo che il runtime possa chiamare sia [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) al termine dell'elaborazione.

## <a name="code-sample"></a>Codice di esempio

Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET. Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando. Il codice per il cmdlet Get-proc di esempio è di dimensioni ridotte, ma usa ancora il runtime di Windows PowerShell e un oggetto .NET esistente, che è sufficiente per renderlo utile. È possibile eseguirne il test per comprendere meglio cosa può fare Get-proc e come può essere usato l'output. Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Avviare Windows PowerShell e ottenere i processi correnti in esecuzione nel computer.

    ```powershell
    get-proc
    ```

    Viene visualizzato l'output seguente:

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Assegnare una variabile ai risultati del cmdlet per una manipolazione più semplice.

    ```powershell
    $p=get-proc
    ```

3. Ottenere il numero di processi.

    ```powershell
    $p.length
    ```

    Viene visualizzato l'output seguente:

    ```output
    63
    ```

4. Recuperare un processo specifico.

    ```powershell
    $p[6]
    ```

    Viene visualizzato l'output seguente:

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Ottiene l'ora di inizio del processo.

    ```powershell
    $p[6].starttime
    ```

    Viene visualizzato l'output seguente:

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Ottenere i processi per i quali il numero di handle è maggiore di 500 e ordinare il risultato.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Viene visualizzato l'output seguente:

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Usare il cmdlet `Get-Member` per elencare le proprietà disponibili per ogni processo.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Viene visualizzato l'output seguente:

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Vedere anche

[Creazione di un cmdlet per elaborare l'input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Creazione di un cmdlet per elaborare l'input della pipeline](./adding-parameters-that-process-pipeline-input.md)

[Come creare un cmdlet di Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Funzionamento di Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)

[Esempi di cmdlet](./cmdlet-samples.md)
