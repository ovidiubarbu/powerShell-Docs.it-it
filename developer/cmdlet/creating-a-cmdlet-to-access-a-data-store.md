---
title: Creazione di un Cmdlet per accedere a una Data Store | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 28d55874960f9a64b986204411d38319ef1d0da7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059525"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Creazione di un cmdlet per accedere a un archivio dati

In questa sezione viene descritto come creare un cmdlet che accede ai dati archiviati tramite un provider di Windows PowerShell. Questo tipo di cmdlet Usa l'infrastruttura del provider di Windows PowerShell del runtime di Windows PowerShell e, pertanto, la classe cmdlet deve derivare dal [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe di base.

Il cmdlet Select-Str descritto di seguito possa individuare e selezionare le stringhe in un file o un oggetto. Gli schemi utilizzati per identificare la stringa possono essere specificati in modo esplicito tramite il `Path` parametri del cmdlet o in modo implicito tramite il `Script` parametro.

Il cmdlet è progettato per utilizzare qualsiasi provider di Windows PowerShell che deriva da [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Ad esempio, il cmdlet è possibile specificare il provider FileSystem o il provider Variable fornita da Windows PowerShell. Per altre informazioni aboutWindows provider PowerShell, vedere [provider di progettazione di Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).

Gli argomenti in questa sezione includono quanto segue:

- [La definizione di classe del Cmdlet](#Defining-the-Cmdlet-Class)

- [Definizione dei parametri per l'accesso ai dati](#Declaring-the-Path-Parameter)

- [Si esegue l'override di metodi di elaborazione dell'Input](#Overriding-Input-Processing-Methods)

- [L'accesso al contenuto](#Accessing-Content)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#Declaring-Search-Support-Parameters)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>La definizione di classe del Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Questo cmdlet rileva alcune stringhe, in modo che il nome del verbo selezionato qui è "Select", definiti per il [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe. Il nome del sostantivo "Str" viene usato perché il cmdlet vengono eseguite operazioni su stringhe. Nella dichiarazione seguente, si noti che il nome del verbo e sostantivo cmdlet vengono riflesse nel nome di classe del cmdlet. Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

La classe .NET per questo cmdlet deve derivare dal [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base, poiché offre il supporto necessario per il runtime di Windows PowerShell per esporre il provider di Windows PowerShell infrastruttura. Si noti che questo cmdlet rende anche usate le classi di espressioni regolari di .NET Framework, quali [RegularExpressions](/dotnet/api/System.Text.RegularExpressions.Regex).

Il codice seguente è la definizione di classe per questo cmdlet Select-Str.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Questo cmdlet definisce un set mediante l'aggiunta di parametri predefiniti di `DefaultParameterSetName` (parola chiave) dell'attributo per la dichiarazione di classe. Il set di parametri predefiniti `PatternParameterSet` viene usato quando il `Script` parametro non è specificato. Per altre informazioni su questo set di parametri, vedere la `Pattern` e `Script` discussione parametro nella sezione seguente.

## <a name="defining-parameters-for-data-access"></a>Definizione dei parametri per l'accesso ai dati

Questo cmdlet consente di definire vari parametri che consentono all'utente di accedere a ed esaminare i dati archiviati. Questi parametri includono un `Path` parametro che indica la posizione dell'archivio dati, un `Pattern` parametro che specifica il modello da utilizzare nella ricerca e molti altri parametri che supportano la modalità in cui viene eseguita la ricerca.

> [!NOTE]
> Per altre informazioni sulle nozioni di base della definizione dei parametri, vedere [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Dichiarare il parametro Path

Per individuare l'archivio dati, questo cmdlet è necessario utilizzare un percorso di Windows PowerShell per identificare il provider di Windows PowerShell che è progettato per l'accesso all'archivio dati. Pertanto, definisce un `Path` parametro di tipo matrice di stringa per indicare il percorso del provider.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Si noti che questo parametro appartiene a due set di parametri diversi e che abbia un alias.

Due [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributi dichiarano che la `Path` appartiene al parametro il `ScriptParameterSet` e il `PatternParameterSet`. Per altre informazioni sui set di parametri, vedere [aggiunta di set di parametri a un Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

Il [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attributo dichiara un `PSPath` alias per il `Path` parametro. La dichiarazione di alias è consigliabile per coerenza con altri cmdlet di accesso ai provider di Windows PowerShell. Per altre informazioni aboutWindows percorsi di PowerShell, vedere "Concetti di percorso di PowerShell" nella [modalità di funzionamento di Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="declaring-the-pattern-parameter"></a>Dichiarare il parametro di modello

Per specificare i modelli per la ricerca, questo cmdlet viene dichiarato un `Pattern` parametro che è una matrice di stringhe. Se uno qualsiasi dei modelli si trovano nell'archivio dati, viene restituito un risultato positivo. Si noti che questi modelli possono essere compilati in una matrice di espressioni regolari compilate o una matrice di modelli con caratteri jolly utilizzati per le ricerche di valore letterale.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Quando viene specificato questo parametro, il cmdlet Usa il set di parametri predefinito `PatternParameterSet`. In questo caso, il cmdlet Usa i modelli specificati qui per selezionare le stringhe. Al contrario, il `Script` parametro può essere utilizzato anche per fornire uno script che contiene i modelli. Il `Script` e `Pattern` parametri definiscono due set di parametri separato, in modo che si escludono a vicenda.

### <a name="declaring-search-support-parameters"></a>La dichiarazione di parametri di supporto di ricerca

Questo cmdlet consente di definire i parametri di supporto seguenti che possono essere utilizzati per modificare le funzionalità di ricerca del cmdlet.

Il `Script` parametro specifica un blocco di script che può essere utilizzato per fornire un meccanismo di ricerca alternativo per il cmdlet. Lo script deve contenere i modelli usati per la corrispondenza e restituire un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) oggetto. Si noti che questo parametro è anche il parametro univoco che identifica il `ScriptParameterSet` set di parametri. Quando il runtime di Windows PowerShell rileva questo parametro, Usa solo i parametri che appartengono al `ScriptParameterSet` set di parametri.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

Il `SimpleMatch` parametro è un parametro opzionale che indica se il cmdlet deve corrispondere in modo esplicito i modelli vengono forniti. Quando l'utente specifica il parametro alla riga di comando (`true`), il cmdlet Usa i modelli come vengono forniti. Se il parametro non viene specificato (`false`), il cmdlet Usa espressioni regolari. Il valore predefinito per questo parametro è `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

Il `CaseSensitive` parametro è un parametro opzionale che indica se viene eseguita una ricerca tra maiuscole e minuscole. Quando l'utente specifica il parametro alla riga di comando (`true`), il cmdlet verifica la presenza di maiuscole e minuscole dei caratteri durante il confronto dei modelli. Se il parametro non viene specificato (`false`), il cmdlet non viene fatta distinzione tra maiuscole e minuscole. Ad esempio "MyFile" e "myfile" verrebbe entrambi restituiti come risultati positivi. Il valore predefinito per questo parametro è `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

Il `Exclude` e `Include` parametri identificano gli elementi che vengono escluse o incluse nella ricerca in modo esplicito. Per impostazione predefinita, il cmdlet eseguirà la ricerca tutti gli elementi nell'archivio dati. Tuttavia, per limitare la ricerca eseguita dal cmdlet, questi parametri possono essere utilizzati per indicare in modo esplicito gli elementi da includere nella ricerca o omesso.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>La dichiarazione di set di parametri

Questo cmdlet usa due set di parametri (`ScriptParameterSet` e `PatternParameterSet`, ovvero il valore predefinito) come nomi dei due set di parametri usato nell'accesso ai dati. `PatternParameterSet` è il set di parametri predefinito e viene usato quando il `Pattern` parametro è specificato. `ScriptParameterSet` viene utilizzato quando l'utente specifica un meccanismo di ricerca alternativo tramite la `Script` parametro. Per altre informazioni sui set di parametri, vedere [aggiunta di set di parametri a un Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Si esegue l'override di metodi di elaborazione dell'Input

I cmdlet devono eseguire l'override uno o più i metodi per l'elaborazione dell'input di [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe. Per altre informazioni sui metodi di elaborazione dell'input, vedere [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

Questo cmdlet esegue l'override di [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) compilato di metodo per compilare una matrice di espressioni regolari all'avvio. Ciò migliora le prestazioni durante le ricerche che non usano la corrispondenza semplice.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

Questo cmdlet sostituisce anche il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per elaborare le selezioni di stringa apportate dall'utente nella riga di comando. Scrive i risultati della selezione di stringa sotto forma di un oggetto personalizzato tramite una chiamata private **corrispondenza** (metodo).

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>L'accesso al contenuto

Il cmdlet deve aprire il provider indicato dal percorso di Windows PowerShell in modo che possa accedere i dati. Il [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) oggetto per lo spazio di esecuzione viene usato per l'accesso al provider, mentre le [System.Management.Automation.PSCmdlet.Invokeprovider*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) proprietà del cmdlet viene utilizzato per aprire il provider. L'accesso al contenuto viene fornito per il recupero dei [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) aprire l'oggetto per il provider.

Questo cmdlet Select-Str di esempio Usa la [System.Management.Automation.Providerintrinsics.Content*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) proprietà per esporre il contenuto da analizzare. Quindi possibile chiamare il [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) , passando il percorso di Windows PowerShell necessari.

## <a name="code-sample"></a>Esempio di codice

Il codice seguente illustra l'implementazione di questa versione di questo cmdlet Select-Str. Si noti che questo codice include la classe cmdlet e metodi privati utilizzati dal cmdlet Windows PowerShell snap-in di codice consente di registrare i cmdlet. Per altre informazioni sulla registrazione dei cmdlet, vedere [compilazione di Cmdlet](#Building-the-Cmdlet).

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. La procedura seguente è utilizzabile per testare il cmdlet Select-Str di esempio.

1. Avviare Windows PowerShell e cercare le occorrenze delle righe con l'espressione ".NET" nel file note. Si noti che virgolette doppie che racchiudono il nome del percorso sono necessarie solo se il percorso è costituito da più di una parola.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    Viene visualizzato l'output seguente.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Cercare nel file note le occorrenze delle righe con la parola "su", seguita da qualsiasi altro testo. Il `SimpleMatch` parametro Usa il valore predefinito di `false`. La ricerca fa distinzione tra maiuscole e perché il `CaseSensitive` parametro è impostato su `false`.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    Viene visualizzato l'output seguente.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. Cercare nel file note usando un'espressione regolare come modello. Il cmdlet cerca di caratteri alfabetici e spazi vuoti, racchiusi tra parentesi.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    Viene visualizzato l'output seguente.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. Eseguire una ricerca tra maiuscole e minuscole del file note per ricercare le occorrenze della parola "Parametro".

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    Viene visualizzato l'output seguente.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. Ricerca il provider variable forniti con Windows PowerShell per le variabili che hanno valori numerici da 0 a 9.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    Viene visualizzato l'output seguente.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Usare un blocco di script per cercare il file SelectStrCommandSample.cs per la stringa "Pos". Il **cmatch** funzionano per lo script esegue una corrispondenza tra maiuscole e minuscole.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    Viene visualizzato l'output seguente.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Vedere anche

[Come creare un Cmdlet di Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Progettare il Provider di Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md)

[Funzionamento di Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
