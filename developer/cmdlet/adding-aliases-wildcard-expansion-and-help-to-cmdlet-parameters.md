---
title: Aggiunta di alias di espansione di caratteri jolly e consentono di parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075257"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Aggiunta di alias, espansione di caratteri jolly e guida per i parametri del cmdlet

In questa sezione viene descritto come aggiungere gli alias, espansione di caratteri jolly, e i messaggi della Guida per i parametri del cmdlet Stop-Process (descritto nella [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)).

Questo cmdlet Stop-Process tenta di arrestare i processi che vengono recuperati usando il cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Gli argomenti in questa sezione includono quanto segue:

- [Che definisce il Cmdlet](#Defining-the-Cmdlet)

- [Definizione dei parametri per la modifica di sistema](#Defining-Parameters-for-System-Modification)

- [La definizione di un Alias del parametro](#Defining-a-Parameter-Alias)

- [Creazione di una Guida per i parametri](#Creating-Help-for-Parameters)

- [Si esegue l'override di un metodo di elaborazione dell'Input](#Overriding-an-Input-Processing-Method)

- [Supporto di espansione di caratteri jolly](#Supporting-Wildcard-Expansion)

- [Esempio di codice](#Defining-a-Parameter-Alias)

- [Definizione di tipi di oggetto e formattazione](#Define-Object-Types-and-Formatting)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Che definisce il Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Poiché si sta scrivendo un cmdlet per modificare il sistema, devono essere denominato di conseguenza. Poiché questo cmdlet arresta i processi di sistema, utilizza il verbo "Stop", definito dal [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), con il sostantivo "Proc" per indicare di processo. Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Il codice seguente è la definizione di classe per questo cmdlet Stop-Process.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definizione dei parametri per la modifica di sistema

Il cmdlet deve definire i parametri che le modifiche di sistema di supporto e commenti degli utenti. Il cmdlet deve definire un `Name` parametro o equivalente in modo che il cmdlet sarà in grado di modificare il sistema da una forma di identificatore. Inoltre, è necessario definire il cmdlet di `Force` e `PassThru` parametri. Per altre informazioni su questi parametri, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>La definizione di un Alias del parametro

Un alias del parametro può essere un nome alternativo o un nome breve di-1 o 2 lettere ben definito per un parametro del cmdlet. In entrambi i casi, l'obiettivo di utilizzo degli alias è per semplificare l'immissione di utente dalla riga di comando. Windows PowerShell supporta gli alias di parametro tramite il [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, che utilizza la sintassi di dichiarazione [Alias()].

Il codice seguente illustra come aggiungere un alias per il `Name` parametro.

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

Oltre a usare il [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attributo, il runtime di Windows PowerShell esegue la corrispondenza nome parziale, anche se non viene specificato alcun alias. Se, ad esempio, il cmdlet dispone di un `FileName` parametro e che è l'unico parametro che inizia con `F`, l'utente potrebbe immettere `Filename`, `Filenam`, `File`, `Fi`, o `F` e riconosce ancora la voce come il `FileName` parametro.

## <a name="creating-help-for-parameters"></a>Creazione di una Guida per i parametri

Windows PowerShell consente di creare la Guida per i parametri del cmdlet. Eseguire questa operazione per qualsiasi parametro usato per il feedback utente e la modifica di sistema. Per ogni parametro per il supporto della Guida, è possibile impostare il `HelpMessage` parola chiave nell'attributo le [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) dichiarazione dell'attributo. Questa parola chiave definisce il testo da visualizzare all'utente per ottenere assistenza tramite il parametro. È anche possibile impostare il `HelpMessageBaseName` parola chiave per identificare il nome di base di una risorsa da usare per il messaggio. Se si imposta questa parola chiave, è necessario impostare anche la `HelpMessageResourceId` (parola chiave) per specificare l'identificatore della risorsa.

Il codice seguente da questo cmdlet Stop-Process definisce il `HelpMessage` attributo la parola chiave per il `Name` parametro.

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

## <a name="overriding-an-input-processing-method"></a>Si esegue l'override di un metodo di elaborazione dell'Input

Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, in genere si tratterà [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Quando si modifica il sistema, è necessario chiamare il cmdlet di [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi per consentire all'utente per fornire commenti e suggerimenti prima viene apportata una modifica. Per altre informazioni su questi metodi, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Supporto di espansione di caratteri jolly

Per consentire la selezione di più oggetti, è possibile usare i cmdlet di [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) alle classi di fornire supporto di espansione con caratteri jolly per il parametro di input. Esempi di modelli con caratteri jolly sono lsa * \*file con estensione txt e [a-c]\*. Quando il modello contiene un carattere che deve essere utilizzato in modo letterale, utilizzare il carattere virgoletta inversa (') come carattere di escape.

Le espansioni con caratteri jolly di nomi di file e percorso sono esempi di scenari comuni in cui il cmdlet potrebbe essere necessario consentire il supporto per gli input di percorso quando è richiesta la selezione di più oggetti. Un caso comune è nel file system, in cui un utente desidera vedere tutti i file che si trovano nella cartella corrente.

È necessario solo raramente un'implementazione corrispondente del modello con caratteri jolly personalizzati. In questo caso, il cmdlet deve supportare la completa 1003.2 POSIX, 3,13 specifica per l'espansione di caratteri jolly o il subset semplificato seguente:

- **Punto interrogativo (?).** Corrisponde a qualsiasi carattere nella posizione specificata.

- **Asterisco (\*).** Corrisponde a zero o più caratteri a partire dalla posizione specificata.

- **Parentesi quadra aperta ([]).** Introduce un'espressione tra parentesi quadre che può contenere caratteri o un intervallo di caratteri. Se è necessario un intervallo di valori, un trattino (-) viene utilizzato per indicare l'intervallo.

- **Parentesi quadra chiusa (]).** Termina un'espressione tra parentesi quadre.

- **Virgoletta carattere di escape (').** Indica che il carattere successivo deve essere considerato letteralmente. Tenere presente che quando si specifica il carattere di virgoletta dalla riga di comando (invece di specificare a livello di codice), il carattere di escape virgoletta deve essere specificato due volte.

> [!NOTE]
> Per altre informazioni sui modelli con caratteri jolly, vedere [che supportano i caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Il codice seguente viene illustrato come impostare le opzioni con caratteri jolly e definire il modello carattere jolly usato per risolvere il `Name` parametro per questo cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Il codice seguente viene illustrato come testare se il nome di processo corrisponde al modello definito con caratteri jolly. Si noti che, in questo caso, se il nome del processo non corrisponde al modello, il cmdlet continua nel ottenere il nome del processo successivo.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [esempio StopProcessSample03](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definire i tipi di oggetto e la formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. È possibile testare il cmdlet Stop-Process di esempio. Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Avviare Windows PowerShell e usare Stop-Process per arrestare un processo usando l'alias ProcessName di `Name` parametro.

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

- Verificare la voce seguente nella riga di comando. Poiché il parametro Name è obbligatorio, richiesto. Immettere "!?" Visualizza il testo della Guida associato al parametro.

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

- Ora apportare la voce seguente per arrestare tutti i processi che corrispondono al modello con caratteri jolly "* Nota\*". Viene chiesto prima di arrestare ciascun processo che corrisponde al modello.

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

[Creare un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Come creare un Cmdlet di Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estensione di tipi di oggetto e la formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Che supportano i caratteri jolly in parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
