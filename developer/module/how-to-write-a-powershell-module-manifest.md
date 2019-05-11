---
title: Come scrivere un manifesto del modulo di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670286"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Come scrivere un manifesto del modulo di PowerShell

Dopo aver scritto il modulo Windows PowerShell, è possibile aggiungere facoltativamente un manifesto del modulo. Un manifesto del modulo è un file di script di PowerShell che è possibile usare per includere informazioni sul modulo. Ad esempio, è possibile descrivere l'autore, specificare i file del modulo (ad esempio, i moduli annidati), eseguirli gli script per personalizzare l'ambiente dell'utente, caricano il tipo e i file di formattazione, definiscono i requisiti di sistema e limitano i membri esportati dal modulo.

## <a name="creating-a-module-manifest"></a>Creazione di un manifesto del modulo

Oggetto *manifesto del modulo* è un file di dati di Windows PowerShell (con estensione psd1) che descrive il contenuto di un modulo e determina la modalità di elaborazione di un modulo. Il file manifesto è un file di testo che contiene una tabella hash di chiavi e valori. Per collegare un file manifesto a un modulo, denominarlo lo stesso come il modulo e inserirlo nella radice della directory del modulo.

Per i moduli semplici che contengono solo un singolo con estensione psm1 o un assembly binario, un manifesto del modulo è facoltativo. Tuttavia, è consigliabile usare un manifesto del modulo quando possibile, perché sono utili che consentono di organizzare il codice e la gestione delle informazioni di controllo delle versioni. Inoltre, per esportare un assembly installato nella global assembly cache è necessario un manifesto del modulo. Un manifesto del modulo è necessario anche per i moduli che supportano la funzionalità Guida aggiornabile. Vale a dire, la Guida aggiornabile Usa la **HelpInfoUri** chiave nel manifesto del modulo per trovare il file di informazioni (HelpInfo XML) della Guida che contiene il percorso dei file della Guida aggiornati per il modulo. Per altre informazioni sulla Guida aggiornabile, vedere [supporto della Guida aggiornabile](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Creare e usare un manifesto del modulo

1. Per creare un manifesto del modulo, sono disponibili diverse opzioni:

   1. Direttamente creare la tabella hash con le informazioni minime necessarie e salvarlo in un file con estensione psd1 con lo stesso nome di un modulo. Dopo che è stato fatto, è possibile aprire il file e aggiungere manualmente i valori appropriati.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. In alternativa, chiamare il [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet, con una o più dei valori predefiniti passati come parametri. (Si noti che il solo nome del file è obbligatorio per generare un manifesto, tuttavia.) Si creerà un manifesto del modulo con tutti i manifesto valori specificati in modo espliciti e con il resto che contiene il valore predefinito.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Infine, è possibile anche creare un file con estensione psd1 vuoto e copiare il modello nella parte inferiore di questo argomento nel file e inserire i valori pertinenti. L'unico requisito effettivo in questo caso sarebbe per garantire che il file è stato assegnato lo stesso nome del modulo.

2. Aggiungere in qualsiasi elemento aggiuntivo per il manifesto nel quale si desidera avere nel file.

   In generale, questo verrà probabilmente eseguito in qualsiasi editor di testo si preferisce, ad esempio Blocco note. Tuttavia questo è tecnicamente un file di script contenente codice, quindi è possibile modificarlo in un ambiente di sviluppo o la creazione di script effettivo, ad esempio PowerShell ISE. Anche in questo caso, si noti che tutti gli elementi di un file manifesto sono facoltativi, eccetto il numero di ModuleVersion.

   Per una descrizione delle chiavi e valori è possibile avere in un manifesto del modulo, vedere la **elementi del manifesto di modulo** sotto. Per altre informazioni, vedere le descrizioni dei parametri in di [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. Facoltativamente, è possibile scrivere codice aggiuntivo per il manifesto del modulo, per risolvere tutti gli scenari che potrebbero non essere analizzati gli elementi del manifesto di modulo di base.

   A causa di problemi di sicurezza, PowerShell verrà eseguito solo un piccolo subset di operazioni disponibili in un file manifesto del modulo. In generale, è possibile usare la **se** istruzione, gli operatori aritmetici e di confronto e i tipi di dati base di PowerShell.

4. Dopo aver creato il manifesto del modulo, è possibile eseguirne il test (per confermare che tutti i percorsi descritti nel manifesto vengono corretti) con una chiamata a [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Assicurarsi che il manifesto del modulo si trova nel primo livello della directory che contiene un modulo.

   Quando si copia un modulo in un sistema e importarlo, PowerShell userà il manifesto del modulo per importare il modulo.

6. Facoltativamente, è possibile testare direttamente il manifesto del modulo con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) da dot-sourcing il manifesto di se stesso.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementi del manifesto di modulo

Nella tabella seguente vengono descritti gli elementi che è possibile avere in un manifesto del modulo

|Elemento|Default|Description|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Tipo: string|' '|Modulo o file binario file modulo di script associati a questo manifesto. Le versioni precedenti di PowerShell chiamato questo elemento di ModuleToProcess.<br /><br /> I tipi possibili per il modulo radice possono essere vuoti (che rendono questa una **manifesto** modulo), il nome di un modulo di script (psm1, rendendo questo un **Script** modulo), o il nome di un modulo binario (.exe o dll, rendendo questo un **binario** modulo). Inserire il nome di un manifesto del modulo (con estensione psd1) o un file di script (con estensione ps1) in questo elemento causerà un errore si verifica.|
|ModuleVersion<br /><br /> Tipo: string|1.0|Numero di versione di questo modulo. La stringa deve essere in grado di convertire in [Version]. Vale a dire, ' &. &. #. #. #'. `Import-Module` verrà caricato il primo modulo consente di trovare nel **$psModulePath** che corrisponde al nome e dispone di almeno così elevati come un ModuleVersion, come il `-MinimumVersion` parametro. Per importare una versione specifica, usare il`-RequiredVersion` parametro, invece.<br /><br /> Esempio: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Tipo: string|GUID generato automaticamente|ID usato per identificare in modo univoco questo modulo. Si noti che non è attualmente possibile importare un modulo da GUID.<br /><br /> Esempio: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autore<br /><br /> Tipo: string|Nessuno|Autore di questo modulo.<br /><br /> Esempio: `Author = 'AuthorNameHere'`|
|CompanyName*<br /><br /> Tipo: string|Unknown|Società o fornitore di questo modulo.<br /><br /> Esempio: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Tipo: string|(c) [currentYear] [creare]. Tutti i diritti sono riservati.|Dichiarazione di copyright per il modulo.<br /><br /> Esempio: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Description<br /><br /> Tipo: string|' '|Descrizione delle funzionalità fornite da questo modulo.<br /><br /> Esempio: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Tipo: string|' '|Versione minima del motore di Windows PowerShell richiesto da questo modulo. Valori validi correnti sono 1.0, 2.0, 3.0, 4.0 e 5.0.<br /><br /> Esempio: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Tipo: string|' '|Specifica il nome dell'host di Windows PowerShell che è necessario il modulo. Questo nome viene fornito da Windows PowerShell. Per trovare il nome di un programma host, nel programma, digitare: `$host.name` .<br /><br /> Esempio: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Tipo: string|' '|Versione minima dell'host di Windows PowerShell richiesto da questo modulo.<br /><br /> Esempio: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Tipo: string|' '|Versione minima di Microsoft .NET Framework richiesta da questo modulo.<br /><br /> Esempio: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Tipo: string|' '|Versione minima di common language runtime (CLR) richiesto da questo modulo.<br /><br /> Esempio: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Tipo: string|' '|Architettura del processore (None, X86, Amd64) richiesto da questo modulo. I valori validi sono x86, AMD64, IA64 e Nessuno (sconosciuto o non specificato).<br /><br /> Esempio: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [string[]]|@()|Moduli che devono essere importati nell'ambiente globale prima di importare questo modulo. Verranno caricati tutti i moduli elencati a meno che non sono già stati caricati. (Ad esempio, alcuni moduli potrebbero già essere caricati da un modulo diverso.). È anche possibile specificare una versione specifica per caricare utilizzando `RequiredVersion` anziché `ModuleVersion`. Quando si usa `ModuleVersion` caricherà la versione più recente disponibile con almeno la versione specificata.<br /><br /> Esempio: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Esempio: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type: [string[]]|@()|Assembly che devono essere caricati prima di importare questo modulo.<br /><br /> Si noti che a differenza di RequiredModules, PowerShell per caricare il RequiredAssemblies se non sono già caricati.|
|ScriptsToProcess<br /><br /> Type: [string[]]|@()|File di script (con estensione ps1) che vengono eseguiti nello stato sessione del chiamante quando viene importato il modulo. Potrebbe trattarsi di sessione globale dello stato o, per i moduli annidati, lo stato della sessione di un altro modulo. È possibile utilizzare questi script per preparare un ambiente esattamente come è possibile usare uno script di accesso.<br /><br /> Questi script vengono eseguiti prima di uno qualsiasi dei moduli elencati nel manifesto vengono caricato.|
|TypesToProcess<br /><br /> Tipo: [oggetto []]|@()|Tipo di file (con estensione PS1XML) da caricare durante l'importazione di questo modulo.|
|FormatsToProcess<br /><br /> Tipo: [oggetto []]|@()|Formato di file (con estensione PS1XML) da caricare durante l'importazione di questo modulo.|
|NestedModules<br /><br /> Tipo: [oggetto []]|@()|Moduli da importare come moduli annidati del modulo specificato in RootModule/ModuleToProcess.<br /><br /> Aggiunta di un nome di modulo per questo elemento è simile alla chiamata `Import-Module` dall'interno del codice di script o l'assembly. La differenza principale è che risulta più semplice visualizzare ciò che si sta caricando qui nel file manifesto. Inoltre, se un modulo non viene caricato in questo caso, verrà non ancora sono stati caricati un modulo effettivo.<br /><br /> Oltre a altri moduli, è inoltre possibile caricare qui i file di script (con estensione ps1). Questi file verranno eseguite nel contesto del modulo radice. (Questo è equivalente a dot sourcing lo script in un modulo radice).|
|FunctionsToExport<br /><br /> Digitare il comando seguente: String|'*'|Specifica le funzioni esportate dal modulo (sono consentiti caratteri jolly) per lo stato della sessione del chiamante. Per impostazione predefinita, vengono esportate tutte le funzioni. È possibile usare questa chiave per limitare le funzioni esportate dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere la sessione globale dello stato o, per i moduli annidati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutte le funzioni esportate da un modulo annidato verranno esportate allo stato sessione globale, a meno che un modulo nella catena limita la funzione con la chiave FunctionsToExport.<br /><br /> Se il manifesto consente inoltre di esportare gli alias per le funzioni, questa chiave consente di rimuovere funzioni il cui alias sono elencati nella chiave AliasesToExport, ma questa chiave non è possibile aggiungere gli alias di funzione all'elenco.|
|CmdletsToExport<br /><br /> Digitare il comando seguente: String|'*'|Specifica i cmdlet esportati dal modulo (sono consentiti caratteri jolly). Per impostazione predefinita, vengono esportati tutti i cmdlet. È possibile usare questa chiave per limitare i cmdlet esportati dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere la sessione globale dello stato o, per i moduli annidati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutti i cmdlet esportati da un modulo annidato verranno esportati in definitiva allo stato sessione globale, a meno che un modulo nella catena limita il cmdlet con la chiave CmdletsToExport.<br /><br /> Se il manifesto consente inoltre di esportare gli alias per i cmdlet, questa chiave consente di rimuovere cmdlet il cui alias sono elencati nella chiave AliasesToExport, ma questa chiave non è possibile aggiungere all'elenco alias di cmdlet.|
|VariablesToExport<br /><br /> Digitare il comando seguente: String|'*'|Specifica le variabili esportate dal modulo (sono consentiti caratteri jolly) per lo stato della sessione del chiamante. Per impostazione predefinita, vengono esportate tutte le variabili. È possibile usare questa chiave per limitare le variabili esportate dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere la sessione globale dello stato o, per i moduli annidati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutte le variabili che vengono esportate da un modulo annidato verranno esportate allo stato sessione globale, a meno che un modulo nella catena limita la variabile utilizzando la chiave VariablesToExport.<br /><br /> Se il manifesto consente inoltre di esportare gli alias per le variabili, questa chiave consente di rimuovere variabili il cui alias sono elencati nella chiave AliasesToExport, ma questa chiave non è possibile aggiungere gli alias di variabile all'elenco.|
|AliasesToExport<br /><br /> Digitare il comando seguente: String|'*'|Specifica gli alias esportati dal modulo (sono consentiti caratteri jolly) per lo stato della sessione del chiamante. Per impostazione predefinita, tutti gli alias vengono esportati. È possibile usare questa chiave per limitare gli alias esportati dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere la sessione globale dello stato o, per i moduli annidati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutti gli alias esportati da un modulo annidato verranno esportati in definitiva allo stato sessione globale, a meno che un modulo nella catena limita l'alias usando la chiave AliasesToExport.|
|ModuleList<br /><br /> Type: [string[]]|@()|Specifica tutti i moduli inclusi nello stesso pacchetto con questo modulo. Questi moduli possono essere immessi in base al nome (una stringa delimitata da virgole) oppure come una tabella hash con le chiavi ModuleName e GUID. La tabella hash può avere anche una chiave ModuleVersion facoltativa. La chiave ModuleList è progettata per agire come inventario di modulo. Questi moduli non vengono elaborati automaticamente.|
|Elenco dei file<br /><br /> Type: [string[]]|@()|Elenco di tutti i file incluso nel pacchetto con questo modulo. Come con ModuleList, FileList consiste nel semplificare come un elenco di inventario e non viene elaborato in caso contrario.|
|PrivateData<br /><br /> Tipo: [object]|' '|Specifica i dati privati che deve essere passato al modulo radice specificato dalla chiave RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Tipo: string|' '|HelpInfo URI di questo modulo.|
|DefaultCommandPrefix<br /><br /> Tipo: string|' '|Prefisso predefinito per i comandi esportati dal modulo. Sostituire il prefisso predefinito con `Import-Module` -prefisso.|

## <a name="sample-module-manifest"></a>Manifesto del modulo di esempio

Manifesto del modulo di esempio seguente mostra le chiavi e valori predefiniti in un manifesto del modulo. In questo esempio viene creato tramite il `New-ModuleManifest` cmdlet di Windows PowerShell 3.0. Quando si creano più moduli, è possibile utilizzare questo cmdlet per creare un modello di manifesto che può quindi essere modificato per i diversi moduli.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
