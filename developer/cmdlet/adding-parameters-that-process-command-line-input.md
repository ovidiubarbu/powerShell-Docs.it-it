---
title: Aggiunta di parametri che elaborano l'input della riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322756"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Aggiunta di parametri che elaborano gli input della riga di comando

Un'origine di input per un cmdlet è la riga di comando. Questo argomento descrive come aggiungere un parametro al cmdlet **Get-proc** , descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md), in modo che il cmdlet possa elaborare l'input dal computer locale in base agli oggetti espliciti passati al cmdlet. Il cmdlet **Get-proc** descritto di seguito recupera i processi in base ai relativi nomi e quindi Visualizza le informazioni sui processi al prompt dei comandi.

## <a name="defining-the-cmdlet-class"></a>Definizione della classe cmdlet

Il primo passaggio nella creazione di cmdlet è la denominazione dei cmdlet e la dichiarazione della classe .NET Framework che implementa il cmdlet. Questo cmdlet recupera le informazioni sul processo, quindi il nome del verbo scelto qui è "Get". (Quasi tutti i tipi di cmdlet in grado di recuperare informazioni possono elaborare l'input della riga di comando). Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Di seguito è illustrata la dichiarazione di classe per il cmdlet **Get-proc** . Informazioni dettagliate su questa definizione sono disponibili nella pagina relativa alla [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Dichiarazione di parametri

Un parametro del cmdlet consente all'utente di fornire input al cmdlet. Nell'esempio seguente **Get-proc** e `Get-Member` sono i nomi dei cmdlet Pipelined e `MemberType` è un parametro per il `Get-Member` cmdlet. Il parametro ha l'argomento "Property".

**PS > Get-proc; `get-member` -MemberType (proprietà)**

Per dichiarare i parametri per un cmdlet, è necessario definire innanzitutto le proprietà che rappresentano i parametri. Nel cmdlet **Get-proc** , l'unico parametro è `Name`, che in questo caso rappresenta il nome dell'oggetto .NET Framework processo da recuperare. Pertanto, la classe cmdlet definisce una proprietà di tipo stringa per accettare una matrice di nomi.

Di seguito è illustrata la Dichiarazione `Name` di parametro per il parametro del cmdlet **Get-proc** .

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Per informare il runtime di Windows PowerShell che questa proprietà è `Name` il parametro, viene aggiunto un attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) alla definizione della proprietà. La sintassi di base per la dichiarazione di questo `[Parameter()]`attributo è.

> [!NOTE]
> Un parametro deve essere contrassegnato in modo esplicito come Public. Parametri non contrassegnati come Public default come Internal e non vengono trovati dal runtime di Windows PowerShell.

Questo cmdlet usa una matrice di stringhe per il `Name` parametro. Se possibile, il cmdlet deve anche definire un parametro come matrice, perché consente al cmdlet di accettare più di un elemento.

#### <a name="things-to-remember-about-parameter-definitions"></a>Aspetti da ricordare sulle definizioni dei parametri

- I nomi di parametro e i tipi di dati predefiniti di Windows PowerShell devono essere riutilizzati il più possibile per garantire la compatibilità del cmdlet con i cmdlet di Windows PowerShell. Se, ad esempio, tutti i cmdlet usano il nome `Id` del parametro predefinito per identificare una risorsa, l'utente potrà facilmente comprendere il significato del parametro, indipendentemente dal cmdlet usato. Fondamentalmente, i nomi di parametro seguono le stesse regole usate per i nomi delle variabili nella Common Language Runtime (CLR). Per ulteriori informazioni sulla denominazione dei parametri, vedere [cmdlet parameter names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell riserva alcuni nomi di parametro per offrire un'esperienza utente coerente. Non usare questi nomi di parametro: `WhatIf` `Verbose`, `Confirm`,, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`e .`OutBuffer` Sono inoltre riservati gli alias seguenti per questi nomi di parametro: `vb` `ea`, `db`,, `ev`, `ov`e `ob`.

- `Name`è un nome di parametro semplice e comune, consigliato per l'uso nei cmdlet. È preferibile scegliere un nome di parametro simile a quello di un nome complesso univoco per un cmdlet specifico e difficile da ricordare.

- I parametri non fanno distinzione tra maiuscole e minuscole in Windows PowerShell, anche se per impostazione predefinita la shell conserva il caso. La distinzione tra maiuscole e minuscole degli argomenti dipende dall'operazione del cmdlet. Gli argomenti vengono passati a un parametro come specificato nella riga di comando.

- Per esempi di altre dichiarazioni di parametro, vedere [parametri dei cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Dichiarazione di parametri come posizionale o con nome

Un cmdlet deve impostare ogni parametro come parametro posizionale o denominato. Entrambi i tipi di parametri accettano argomenti singoli, più argomenti separati da virgole e impostazioni booleane. Un parametro booleano, detto anche *opzione*, gestisce solo le impostazioni booleane. L'opzione viene usata per determinare la presenza del parametro. Il valore predefinito consigliato `false`è.

Il cmdlet **Get-proc** di esempio definisce `Name` il parametro come parametro posizionale con la posizione 0. Questo significa che il primo argomento immesso dall'utente nella riga di comando viene inserito automaticamente per questo parametro. Se si vuole definire un parametro denominato, per il quale l'utente deve specificare il nome del parametro dalla riga di comando, lasciare `Position` la parola chiave dalla dichiarazione di attributo.

> [!NOTE]
> A meno che non sia necessario denominare i parametri, è consigliabile rendere posizionali i parametri più usati in modo che gli utenti non debbano digitare il nome del parametro.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Dichiarazione dei parametri come obbligatoria o facoltativa

Un cmdlet deve impostare ogni parametro come parametro facoltativo o obbligatorio. Nel cmdlet **Get-proc** di esempio, il `Name` parametro viene definito come facoltativo perché la `Mandatory` parola chiave non è impostata nella dichiarazione dell'attributo.

## <a name="supporting-parameter-validation"></a>Supporto della convalida di parametri

Il cmdlet **Get-proc** di esempio aggiunge un attributo di convalida di input, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute) `Name` , al parametro per abilitare la convalida che l' `null` input non sia né vuoto. Questo attributo è uno dei diversi attributi di convalida forniti da Windows PowerShell. Per esempi di altri attributi di convalida, vedere [convalida dell'input dei parametri](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Override di un metodo di elaborazione dell'input

Se il cmdlet prevede di gestire l'input della riga di comando, deve eseguire l'override dei metodi di elaborazione dell'input appropriati. I metodi di elaborazione dell'input di base sono introdotti nella [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).

Il cmdlet **Get-proc** esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) per `Name` gestire l'input del parametro fornito dall'utente o da uno script. Questo metodo ottiene i processi per ogni nome di processo richiesto oppure tutti per i processi se non viene specificato alcun nome. Si noti che in [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)la chiamata a [System. Management. Automation. cmdlet. WriteObject% 28System. Object% 2CSystem. Boolean% 29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) è il meccanismo di output per l'invio di oggetti di output al cmdlet pipeline. Il secondo parametro della chiamata, `enumerateCollection`, è `true` impostato su per informare il runtime di Windows PowerShell di enumerare la matrice di output degli oggetti processo e scrivere un processo alla volta nella riga di comando.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Esempio di codice

Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Windows PowerShell passa informazioni tra i cmdlet usando oggetti .NET Framework. Di conseguenza, un cmdlet potrebbe avere la necessità di definire un proprio tipo oppure un cmdlet potrebbe dover estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo aver implementato un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet viene registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando. Ecco due modi per testare il codice per il cmdlet di esempio. Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Al prompt di Windows PowerShell usare il comando seguente per elencare il processo di Internet Explorer, denominato "IEXPLORE".

    ```powershell
    PS> get-proc -name iexplore
    ```

Viene visualizzato l'output seguente.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Per elencare i processi di Internet Explorer, Outlook e Notepad denominati "IEXPLORE", "OUTLOOK" e "NOTEPAD", utilizzare il comando seguente. Se sono presenti più processi, vengono visualizzati tutti.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

Viene visualizzato l'output seguente.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri che elaborano l'input della pipeline](./adding-parameters-that-process-pipeline-input.md)

[Creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estensione di tipi di oggetti e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare cmdlet, provider e applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)

[Esempi di cmdlet](./cmdlet-samples.md)
