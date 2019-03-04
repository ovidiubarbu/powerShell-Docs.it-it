---
title: Aggiunta di parametri che elaborano gli Input della riga di comando | Microsoft Docs
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
ms.openlocfilehash: e010e28ec705932063bb418b260a1087fc3eef9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856007"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Aggiunta di parametri che elaborano gli input della riga di comando

Un'origine di input per un cmdlet è la riga di comando. In questo argomento viene descritto come aggiungere un parametro per il **Get-Proc** cmdlet (descritto in [creare il primo Cmdlet](./creating-a-cmdlet-without-parameters.md)) in modo che il cmdlet può elaborare l'input dal computer locale basato su esplicita gli oggetti passati al cmdlet. Il **Get-Proc** cmdlet descritto qui recupera processi basati sui relativi nomi e quindi Visualizza informazioni sui processi in un prompt dei comandi.

Le sezioni seguenti sono in questo argomento:

- [La definizione di classe del Cmdlet](#Defining-the-Cmdlet-Class)

- [Dichiarazione dei parametri](#Declaring-Parameters)

- [Convalida dei parametri di supporto](#Supporting-Parameter-Validation)

- [Si esegue l'override di un metodo di elaborazione dell'Input](#Overriding-an-Input-Processing-Method)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#Defining-Object-Types-and-Formatting)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>La definizione di classe del Cmdlet

Il primo passaggio nella creazione di cmdlet è la denominazione dei cmdlet e la dichiarazione della classe .NET Framework che implementa il cmdlet. Questo cmdlet recupera le informazioni sul processo, in modo che il nome del verbo selezionato qui è "Get". (Quasi una sorta di cmdlet che è in grado di recuperare le informazioni può elaborare input della riga di comando). Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Ecco la dichiarazione di classe per il **Get-Proc** cmdlet. Informazioni su questa definizione sono disponibili nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Dichiarazione dei parametri

Un parametro del cmdlet consente all'utente di fornire l'input al cmdlet. Nell'esempio riportato di seguito **Get-Proc** e `Get-Member` sono i nomi dei cmdlet da pipeline, e `MemberType` è un parametro per il `Get-Member` cmdlet. Il parametro è l'argomento "proprietà".

**PS > get-Process; `get-member` membertype - proprietà**

Per dichiarare i parametri per un cmdlet, è innanzitutto necessario definire le proprietà che rappresentano i parametri. Nel **Get-Proc** è l'unico parametro di cmdlet, `Name`, che in questo caso rappresenta il nome dell'oggetto processo .NET Framework da recuperare. Pertanto, la classe cmdlet definisce una proprietà di tipo stringa per accettare una matrice di nomi.

Di seguito è riportata la dichiarazione di parametro per il `Name` parametro il **Get-Proc** cmdlet.

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

Informare il runtime di Windows PowerShell che questa proprietà è il `Name` parametro, un [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributo viene aggiunto alla definizione della proprietà. La sintassi di base per la dichiarazione di questo attributo è `[Parameter()]`.

> [!NOTE]
> Un parametro deve essere esplicitamente contrassegnato come pubblico. Parametri non contrassegnati come pubblici impostati come interni e non vengono rilevati dal runtime di Windows PowerShell.

Questo cmdlet Usa una matrice di stringhe per il `Name` parametro. Se possibile, i cmdlet devono definire anche un parametro come una matrice, poiché ciò consente al cmdlet accettare più di un elemento.

#### <a name="things-to-remember-about-parameter-definitions"></a>Aspetti da ricordare sulle definizioni dei parametri

- Devono essere riutilizzati quanto più possibile per garantire che sia compatibile con i cmdlet di Windows PowerShell il cmdlet Windows PowerShell parametro dati e i nomi dei tipi predefiniti. Ad esempio, se tutti i cmdlet usano lo `Id` nome del parametro per identificare una risorsa, l'utente sarà facilmente comprendere il significato del parametro, indipendentemente dalle quali cmdlet usano. In pratica, i nomi dei parametri seguono le stesse regole utilizzate per i nomi delle variabili in common language runtime (CLR). Per altre informazioni sulla denominazione dei parametri, vedere [i nomi dei parametri di Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell si riserva alcuni nomi di parametro per fornire un'esperienza utente coerente. Non usare questi nomi di parametro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, e `OutBuffer`. Inoltre, sono riservati i seguenti alias per questi nomi di parametro: `vb`, `db`, `ea`, `ev`, `ov`, e `ob`.

- `Name` è un nome di parametri semplici e comuni consigliato per l'uso in dei cmdlet. È preferibile scegliere un nome di parametro simile al seguente rispetto a un nome di tipo complesso difficili da ricordare e univoco per un cmdlet specifico.

- I parametri sono tra maiuscole e minuscole in Windows PowerShell, anche se per impostazione predefinita della shell preserva le maiuscole e. Distinzione maiuscole/minuscole degli argomenti dipende dall'operazione del cmdlet. Gli argomenti vengono passati a un parametro come specificato nella riga di comando.

- Per esempi di altre dichiarazioni di parametro, vedere [parametri del Cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Dichiarando i parametri come posizionali o denominati

Un cmdlet è necessario impostare ogni parametro come un parametro posizionale o denominato. Entrambi i tipi di parametri di accettare argomenti singoli, più argomenti separati da virgole e le impostazioni booleane. Un parametro booleano, detto anche un *commutatore*, gestisce solo le impostazioni booleane. L'opzione viene utilizzata per determinare la presenza del parametro. Il valore predefinito consigliato è `false`.

L'esempio **Get-Proc** cmdlet definisce il `Name` parametro come un parametro posizionale con posizione 0. Ciò significa che il primo argomento, che l'utente immette nella riga di comando viene inserito automaticamente per questo parametro. Se si desidera definire un parametro denominato, per cui l'utente deve specificare il nome del parametro dalla riga di comando, lasciare il `Position` parola chiave dalla dichiarazione di attributo.

> [!NOTE]
> A meno che non devono essere denominati parametri, si consiglia di apportare posizionali i parametri più usate in modo che gli utenti non dovranno digitare il nome del parametro.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Dichiarazione dei parametri come obbligatori o facoltativi

Un cmdlet è necessario impostare ogni parametro come facoltativo o un parametro obbligatorio. Nell'esempio **Get-Proc** cmdlet, la `Name` parametro è definito come facoltativo, poiché il `Mandatory` parola chiave non è impostata nella dichiarazione dell'attributo.

## <a name="supporting-parameter-validation"></a>Convalida dei parametri di supporto

L'esempio **Get-Proc** cmdlet aggiunge un attributo di convalida dell'input [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), al `Name` parametro per abilitare la convalida che la input non è né `null` né vuoto. Questo attributo è uno dei diversi attributi di convalida forniti da Windows PowerShell. Per esempi degli altri attributi di convalida, vedere [convalida Input parametro](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Si esegue l'override di un metodo di elaborazione dell'Input

Se il cmdlet deve gestire l'input della riga di comando, deve eseguire l'override di metodi di elaborazione dell'input appropriati. In cui sono stati introdotti i metodi di elaborazione dell'input di base [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

Il **Get-Proc** cmdlet sostituisce il [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per gestire il `Name` input del parametro fornito dall'utente o uno script. Questo metodo ottiene i processi per ogni nome di processo richiesto oppure tutti per i processi se viene fornito alcun nome. Si noti che in [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la chiamata a [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) è riportato l'output meccanismo per l'invio di output oggetti alla pipeline. Il secondo parametro di questa chiamata `enumerateCollection`, è impostato su `true` informare il runtime di Windows PowerShell per enumerare la matrice di output degli oggetti processo e scrivere un solo processo alla volta nella riga di comando.

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

Per l'intero C# esempi di codice, vedere [GetProcessSample02 campione](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Windows PowerShell passa informazioni tra i cmdlet utilizzando gli oggetti di .NET Framework. Di conseguenza, un cmdlet potrebbe essere necessario definire un tipo specifico o un cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo aver implementato un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet viene registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. Esistono due modi per testare il codice per il cmdlet di esempio. Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Al prompt di Windows PowerShell, usare il comando seguente per elencare il processo di Internet Explorer, che è denominato "IEXPLORE."

    ```powershell
    PS> get-proc -name iexplore
    ```

Viene visualizzato l'output seguente.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Per elencare i processi di Internet Explorer, Outlook e il blocco note, denominati "IEXPLORE", "OUTLOOK" e "NOTEPAD", usare il comando seguente. Se sono presenti più processi, vengono visualizzati tutti gli elementi.

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

[Aggiunta di parametri di Input della Pipeline di processo](./adding-parameters-that-process-pipeline-input.md)

[Creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)

[Esempi di cmdlet](./cmdlet-samples.md)
