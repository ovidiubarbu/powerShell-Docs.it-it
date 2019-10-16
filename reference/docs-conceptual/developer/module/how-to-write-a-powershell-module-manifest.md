---
title: Come scrivere un manifesto del modulo PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367100"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Come scrivere un manifesto del modulo di PowerShell

Una volta scritto il modulo di Windows PowerShell, è possibile aggiungere facoltativamente un manifesto del modulo. Un manifesto del modulo è un file di script di PowerShell che è possibile usare per includere informazioni sul modulo. Ad esempio, è possibile descrivere l'autore, specificare i file nel modulo, ad esempio i moduli annidati, eseguire script per personalizzare l'ambiente dell'utente, caricare i file di tipo e di formattazione, definire i requisiti di sistema e limitare i membri esportati dal modulo.

## <a name="creating-a-module-manifest"></a>Creazione di un manifesto del modulo

Un *manifesto del modulo* è un file di dati di Windows PowerShell (con estensione psd1) che descrive il contenuto di un modulo e determina la modalità di elaborazione di un modulo. Il file manifesto è un file di testo che contiene una tabella hash di chiavi e valori. Per collegare un file manifesto a un modulo, assegnargli un nome identico al modulo e inserirlo nella radice della directory del modulo.

Per i moduli semplici che contengono solo un singolo assembly psm1 o binario, un manifesto del modulo è facoltativo. Tuttavia, è consigliabile utilizzare un manifesto del modulo quando possibile, poiché sono utili per organizzare il codice e mantenere le informazioni sul controllo delle versioni. Inoltre, per esportare un assembly installato nel Global Assembly Cache è necessario un manifesto del modulo. Un manifesto del modulo è necessario anche per i moduli che supportano la funzionalità Guida aggiornabile. Questo significa che la guida aggiornabile usa la chiave **HelpInfoUri** nel manifesto del modulo per trovare il file di informazioni della guida (HELPINFO XML) che contiene il percorso dei file della Guida aggiornati per il modulo. Per ulteriori informazioni sulla guida aggiornabile, vedere Supporto per la [Guida aggiornabile](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Per creare e utilizzare un manifesto del modulo

1. Per creare un manifesto del modulo, sono disponibili diverse opzioni:

   1. Creare direttamente la tabella hash con le informazioni minime necessarie e salvarla in un file con estensione psd1 con lo stesso nome del modulo. Una volta completata questa operazione, è possibile aprire il file e aggiungere manualmente i valori appropriati.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. In alternativa, chiamare il cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) , con uno o più valori predefiniti passati come parametri. Si noti che, tuttavia, per generare un manifesto è necessario solo il nome del file. Verrà creato un manifesto del modulo con tutti i valori del manifesto specificati in modo esplicito e con il resto che contiene il valore predefinito appropriato.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Infine, è anche possibile creare un file con estensione psd1 vuoto e copiare il modello nella parte inferiore di questo argomento nel file e inserire i valori pertinenti. In questo caso, l'unico requisito reale consiste nel verificare che il nome del file sia uguale a quello del modulo.

2. Aggiungere eventuali elementi aggiuntivi al manifesto che si desidera includere nel file.

   In generale, questa operazione verrà probabilmente eseguita in qualsiasi editor di testo preferito, ad esempio Blocco note. Tuttavia, tecnicamente si tratta di un file di script che contiene codice, pertanto può essere necessario modificarlo in un ambiente di scripting o di sviluppo effettivo, ad esempio Visual Studio Code. Si noti che tutti gli elementi di un file manifesto sono facoltativi, ad eccezione del numero ModuleVersion.

   Per le descrizioni delle chiavi e dei valori che è possibile avere in un manifesto del modulo, vedere gli **elementi del manifesto del modulo** di seguito. Per ulteriori informazioni, vedere le descrizioni dei parametri nel cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

3. Facoltativamente, è possibile scegliere di aggiungere codice aggiuntivo al manifesto del modulo per risolvere gli eventuali scenari che non verrebbero trattati dagli elementi del manifesto del modulo di base.

   A causa dei problemi di sicurezza, PowerShell eseguirà solo un piccolo subset delle operazioni disponibili in un file manifesto del modulo. In genere, è possibile usare l'istruzione **if** , gli operatori aritmetici e di confronto e i tipi di dati di base di PowerShell.

4. Dopo aver creato il manifesto del modulo, è possibile testarlo (per verificare che tutti i percorsi descritti nel manifesto siano corretti) con una chiamata a [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Assicurarsi che il manifesto del modulo si trovi nel primo livello della directory che contiene il modulo.

   Quando si copia il modulo su un sistema e lo si importa, PowerShell userà il manifesto del modulo per importare il modulo.

6. Facoltativamente, è possibile testare direttamente il manifesto del modulo con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) tramite il punto di sourcing del manifesto stesso.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementi del manifesto del modulo

La tabella seguente descrive gli elementi che è possibile avere in un manifesto del modulo

|Elemento|Valore predefinito|Description|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Tipo: stringa|' '|File del modulo di script o del modulo binario associato a questo manifesto. Le versioni precedenti di PowerShell denominavano questo elemento ModuleToProcess.<br /><br /> I tipi possibili per il modulo radice possono essere vuoti (che renderà questo modulo **manifesto** ), il nome di un modulo di script (con estensione psm1, che rende questo modulo di **script** ) o il nome di un modulo binario (con estensione exe o dll che rende questo modulo **binario** ). Se si inserisce il nome di un manifesto del modulo (con estensione psd1) o di un file di script (con estensione ps1) in questo elemento, si verificherà un errore.|
|ModuleVersion<br /><br /> Tipo: stringa|1.0|Numero di versione del modulo. La stringa deve essere in grado di eseguire la conversione a [System. Version]. Ovverò #. #. #. #. #'. `Import-Module` caricherà il primo modulo rilevato nell' **$psModulePath** che corrisponde al nome e dispone almeno di un valore ModuleVersion come il parametro `-MinimumVersion`. Per importare una versione specifica, usare invece il parametro @ no__t-0.<br /><br /> Esempio: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Tipo: stringa|GUID generato automaticamente|ID usato per identificare in modo univoco il modulo. Si noti che non è attualmente possibile importare un modulo per GUID.<br /><br /> Esempio: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autore<br /><br /> Tipo: stringa|Nessuno|Autore del modulo.<br /><br /> Esempio: `Author = 'AuthorNameHere'`|
|CompanyName*<br /><br /> Tipo: stringa|Unknown|Società o fornitore di questo modulo.<br /><br /> Esempio: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Tipo: stringa|(c) [currentYear] [autore]. Tutti i diritti sono riservati.|Dichiarazione del copyright per questo modulo.<br /><br /> Esempio: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Description<br /><br /> Tipo: stringa|' '|Descrizione della funzionalità fornita da questo modulo.<br /><br /> Esempio: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Tipo: stringa|' '|Versione minima del motore di Windows PowerShell richiesta da questo modulo. I valori validi correnti sono 1,0, 2,0, 3,0, 4,0 e 5,0.<br /><br /> Esempio: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Tipo: stringa|' '|Specifica il nome dell'host di Windows PowerShell richiesto dal modulo. Questo nome viene fornito da Windows PowerShell. Per trovare il nome di un programma host, nel programma digitare: `$host.name`.<br /><br /> Esempio: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Tipo: stringa|' '|Versione minima dell'host di Windows PowerShell richiesto da questo modulo.<br /><br /> Esempio: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Tipo: stringa|' '|Versione minima di Microsoft .NET Framework richiesta da questo modulo.<br /><br /> Esempio: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Tipo: stringa|' '|Versione minima del Common Language Runtime (CLR) richiesta da questo modulo.<br /><br /> Esempio: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Tipo: stringa|' '|Architettura del processore (nessuno, x86, amd64) richiesta da questo modulo. I valori validi sono x86, AMD64, IA64 e Nessuno (sconosciuto o non specificato).<br /><br /> Esempio: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Tipo: [String []]|@()|Moduli che devono essere importati nell'ambiente globale prima di importare il modulo. Verranno caricati tutti i moduli elencati a meno che non siano già stati caricati. Alcuni moduli potrebbero, ad esempio, essere già stati caricati da un modulo diverso. È anche possibile specificare una versione specifica da caricare utilizzando `RequiredVersion` anziché `ModuleVersion`. Quando si usa `ModuleVersion`, caricherà la versione più recente disponibile con almeno la versione specificata.<br /><br /> Esempio: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Esempio: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Tipo: [String []]|@()|Assembly che devono essere caricati prima di importare il modulo.<br /><br /> Si noti che a differenza di RequiredModules, PowerShell caricherà il RequiredAssemblies se non sono già stati caricati.|
|ScriptsToProcess<br /><br /> Tipo: [String []]|@()|File di script (con estensione ps1) che vengono eseguiti nello stato sessione del chiamante quando viene importato il modulo. Potrebbe trattarsi dello stato della sessione globale o, per i moduli nidificati, dello stato della sessione di un altro modulo. È possibile usare questi script per preparare un ambiente Analogamente a come si può usare uno script di accesso.<br /><br /> Questi script vengono eseguiti prima del caricamento di uno dei moduli elencati nel manifesto.|
|TypesToProcess<br /><br /> Tipo: [String []]|@()|Digitare i file (con estensione ps1xml) da caricare durante l'importazione del modulo.|
|FormatsToProcess<br /><br /> Tipo: [String []]|@()|Formattare i file (con estensione ps1xml) da caricare durante l'importazione del modulo.|
|NestedModules<br /><br /> Tipo: [String []]|@()|Moduli da importare come moduli annidati del modulo specificato in RootModule/ModuleToProcess.<br /><br /> L'aggiunta di un nome di modulo a questo elemento è simile alla chiamata di `Import-Module` dallo script o dal codice assembly. La differenza principale consiste nel fatto che è più semplice vedere ciò che si sta caricando nel file manifesto. Se, inoltre, un modulo non viene caricato in questo punto, non è ancora stato caricato il modulo effettivo.<br /><br /> Oltre ad altri moduli, è anche possibile caricare i file di script (con estensione ps1) qui. Questi file vengono eseguiti nel contesto del modulo radice. Equivale a punteggiare lo script nel modulo radice.|
|FunctionsToExport<br /><br /> Tipo: [String []]|@()|Specifica le funzioni esportate dal modulo (i caratteri jolly sono consentite ma sconsigliate) allo stato della sessione del chiamante. Per impostazione predefinita, non viene esportata alcuna funzione. È possibile usare questa chiave per elencare le funzioni esportate dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutte le funzioni esportate da un modulo annidato verranno esportate nello stato sessione globale, a meno che un modulo nella catena non limiti la funzione tramite la chiave FunctionsToExport.<br /><br /> Se il manifesto esporta anche alias per le funzioni, questa chiave può rimuovere le funzioni i cui alias sono elencati nella chiave AliasesToExport, ma questa chiave non può aggiungere alias di funzione all'elenco.|
|CmdletsToExport<br /><br /> Tipo: [String []]|@()|Specifica i cmdlet esportati dal modulo (i caratteri jolly sono consentiti ma sconsigliati). Per impostazione predefinita, non viene esportato alcun cmdlet. È possibile usare questa chiave per elencare i cmdlet che vengono esportati dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutti i cmdlet esportati da un modulo annidato verranno infine esportati nello stato sessione globale, a meno che un modulo nella catena non limiti il cmdlet tramite la chiave CmdletsToExport.<br /><br /> Se il manifesto esporta anche alias per i cmdlet, questa chiave può rimuovere i cmdlet i cui alias sono elencati nella chiave AliasesToExport, ma questa chiave non può aggiungere alias di cmdlet all'elenco.|
|VariablesToExport<br /><br /> Tipo: stringa|'*'|Specifica le variabili esportate dal modulo (sono consentiti caratteri jolly) per lo stato della sessione del chiamante. Per impostazione predefinita, vengono esportate tutte le variabili. È possibile usare questa chiave per limitare le variabili esportate dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutte le variabili esportate da un modulo annidato verranno esportate nello stato sessione globale, a meno che un modulo nella catena non limiti la variabile utilizzando la chiave VariablesToExport.<br /><br /> Se il manifesto esporta anche alias per le variabili, questa chiave può rimuovere le variabili i cui alias sono elencati nella chiave AliasesToExport, ma questa chiave non può aggiungere alias di variabile all'elenco.|
|AliasesToExport<br /><br /> Tipo: [String []]|@()|Specifica gli alias esportati dal modulo (i caratteri jolly sono consentiti ma sconsigliati) allo stato della sessione del chiamante. Per impostazione predefinita, non viene esportato alcun alias. È possibile usare questa chiave per elencare gli alias esportati dal modulo.<br /><br /> Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutti gli alias esportati da un modulo annidato verranno infine esportati nello stato sessione globale, a meno che un modulo nella catena non limiti l'alias tramite la chiave AliasesToExport.|
|Modulo di<br /><br /> Tipo: [String []]|@()|Specifica tutti i moduli inclusi in un pacchetto con questo modulo. Questi moduli possono essere immessi in base al nome (una stringa con valori delimitati da virgole) o come tabella hash con le chiavi ModuleName e GUID. La tabella hash può anche avere una chiave ModuleVersion facoltativa. La chiave del modulo è progettata per fungere da inventario dei moduli. Questi moduli non vengono elaborati automaticamente.|
|FileList<br /><br /> Tipo: [String []]|@()|Elenco di tutti i file inclusi in questo modulo. Come per l'elenco di moduli, l'elenco di file è utile come elenco di inventario e non viene elaborato in altro modo.|
|PrivateData<br /><br /> Tipo: [oggetto]|@{...}|Specifica i dati privati che devono essere passati al modulo radice specificato dalla chiave RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Tipo: stringa|' '|URI HelpInfo del modulo.|
|DefaultCommandPrefix<br /><br /> Tipo: stringa|' '|Prefisso predefinito per i comandi esportati da questo modulo. Eseguire l'override del prefisso predefinito utilizzando `Import-Module`-prefix.|

## <a name="sample-module-manifest"></a>Manifesto del modulo di esempio

Il manifesto del modulo di esempio seguente mostra le chiavi e i valori predefiniti in un manifesto del modulo. Questo esempio è stato creato con il cmdlet `New-ModuleManifest` in Windows PowerShell 3,0. Quando si creano più moduli, è possibile usare questo cmdlet per creare un modello di manifesto che può quindi essere modificato per i diversi moduli.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
