---
title: Aggiunta di alias, espansione con caratteri jolly e guida ai parametri dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415650"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Aggiunta di alias, espansione di caratteri jolly e guida per i parametri del cmdlet

In questa sezione viene descritto come aggiungere alias, espansione con caratteri jolly e messaggi della Guida ai parametri del cmdlet Stop-proc (descritto in [creazione di un cmdlet che modifica il sistema](./creating-a-cmdlet-that-modifies-the-system.md)).

Questo cmdlet Stop-proc tenta di arrestare i processi recuperati tramite il cmdlet Get-proc, descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).

## <a name="defining-the-cmdlet"></a>Definizione del cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet. Poiché si sta scrivendo un cmdlet per modificare il sistema, è necessario denominarlo di conseguenza. Poiché questo cmdlet interrompe i processi di sistema, usa il verbo "Stop", definito dalla classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con il sostantivo "proc" per indicare il processo. Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Il codice seguente è la definizione di classe per questo cmdlet Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definizione dei parametri per la modifica del sistema

Il cmdlet deve definire i parametri che supportano le modifiche del sistema e il feedback dell'utente. Il cmdlet deve definire un parametro di `Name` o un valore equivalente, in modo che il cmdlet possa modificare il sistema con un tipo di identificatore. Inoltre, il cmdlet deve definire i parametri `Force` e `PassThru`. Per ulteriori informazioni su questi parametri, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definizione di un alias di parametro

Un alias di parametro può essere un nome alternativo o un nome breve con una lettera o un nome breve di due lettere per un parametro del cmdlet. In entrambi i casi, l'obiettivo dell'utilizzo degli alias consiste nel semplificare la voce utente dalla riga di comando. Windows PowerShell supporta gli alias di parametro tramite l'attributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , che usa la sintassi di dichiarazione [alias ()].

Nel codice seguente viene illustrato come aggiungere un alias al parametro `Name`.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Oltre a usare l'attributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) , il runtime di Windows PowerShell esegue la corrispondenza parziale dei nomi, anche se non è specificato alcun alias. Se, ad esempio, il cmdlet dispone di un parametro `FileName` ed è l'unico parametro che inizia con `F`, l'utente può immettere `Filename`, `Filenam`, `File`, `Fi`o `F` e riconoscerne la voce come parametro di `FileName`.

## <a name="creating-help-for-parameters"></a>Creazione della Guida per i parametri

Windows PowerShell consente di creare una guida per i parametri dei cmdlet. Eseguire questa operazione per qualsiasi parametro usato per la modifica del sistema e il feedback dell'utente. Per ogni parametro per supportare la guida, è possibile impostare la parola chiave `HelpMessage` attribute nella dichiarazione di attributo [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Questa parola chiave definisce il testo da visualizzare all'utente per ottenere assistenza nell'uso del parametro. È inoltre possibile impostare la parola chiave `HelpMessageBaseName` per identificare il nome di base di una risorsa da utilizzare per il messaggio. Se si imposta questa parola chiave, è necessario impostare anche la parola chiave `HelpMessageResourceId` per specificare l'identificatore della risorsa.

Il codice seguente di questo cmdlet Stop-proc definisce la parola chiave dell'attributo `HelpMessage` per il parametro `Name`.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Override di un metodo di elaborazione dell'input

Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, più spesso sarà [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Quando si modifica il sistema, il cmdlet deve chiamare i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) per consentire all'utente di fornire feedback prima che venga apportata una modifica. Per ulteriori informazioni su questi metodi, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Supporto dell'espansione con caratteri jolly

Per consentire la selezione di più oggetti, il cmdlet può usare le classi [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) per fornire supporto per l'espansione dei caratteri jolly per l'input dei parametri. Esempi di modelli con caratteri jolly sono LSA *, \*. txt e [a-c]\*. Usare il carattere virgoletta indietro (') come carattere di escape quando il pattern contiene un carattere che deve essere usato letteralmente.

Le espansioni con caratteri jolly di nomi di file e percorsi sono esempi di scenari comuni in cui il cmdlet può volere supportare gli input di percorso quando è richiesta la selezione di più oggetti. Un caso comune è nel file system, in cui un utente desidera visualizzare tutti i file che risiedono nella cartella corrente.

Dovrebbe essere necessaria un'implementazione di criteri di ricerca con caratteri jolly personalizzata solo raramente. In questo caso, il cmdlet deve supportare la specifica POSIX 1003,2, 3,13 completa per l'espansione con caratteri jolly o il subset semplificato seguente:

- **Punto interrogativo (?).** Corrisponde a qualsiasi carattere nella posizione specificata.

- **Asterisco (\*).** Trova la corrispondenza di zero o più caratteri a partire dalla posizione specificata.

- **Parentesi aperta ([).** Introduce un'espressione tra parentesi quadre che può contenere caratteri o un intervallo di caratteri. Se è necessario un intervallo, viene usato un segno meno (-) per indicare l'intervallo.

- **Parentesi chiusa (]).** Termina un'espressione di parentesi quadre.

- **Carattere di escape tra virgolette (').** Indica che il carattere successivo deve essere effettivamente utilizzato. Tenere presente che quando si specifica il carattere di virgolette indietro dalla riga di comando, anziché specificarlo a livello di codice, il carattere di escape per virgolette doppie deve essere specificato due volte.

> [!NOTE]
> Per ulteriori informazioni sui modelli con caratteri jolly, vedere [supporto dei caratteri jolly nei parametri del cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Nel codice seguente viene illustrato come impostare le opzioni con caratteri jolly e come definire il modello con caratteri jolly utilizzato per la risoluzione del parametro `Name` per questo cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Il codice seguente illustra come verificare se il nome del processo corrisponde al modello con caratteri jolly definito. Si noti che, in questo caso, se il nome del processo non corrisponde al modello, il cmdlet continua in per ottenere il nome del processo successivo.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Esempio di codice

Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample03](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definire i tipi di oggetto e la formattazione

Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET. Di conseguenza, un cmdlet può avere la necessità di definire un proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando. Testare il cmdlet di esempio Stop-proc. Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Avviare Windows PowerShell e usare stop-proc per arrestare un processo usando l'alias ProcessName per il parametro `Name`.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Viene visualizzato l'output seguente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Eseguire la voce seguente nella riga di comando. Poiché il parametro Name è obbligatorio, viene richiesto. Immissione di "!?" Visualizza il testo della Guida associato al parametro.

    ```powershell
    PS> stop-proc
    ```

Viene visualizzato l'output seguente.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- A questo punto, effettuare la seguente voce per arrestare tutti i processi che corrispondono al modello con caratteri jolly "* Nota\*". Viene richiesto prima di arrestare ogni processo che corrisponde al modello.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Viene visualizzato l'output seguente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Viene visualizzato l'output seguente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Viene visualizzato l'output seguente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Vedere anche

[Creare un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Come creare un cmdlet di Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))

[Supporto dei caratteri jolly nei parametri dei cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
