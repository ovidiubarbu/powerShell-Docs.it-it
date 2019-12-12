---
title: Come scrivere un manifesto del modulo PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 4aa6c020cf0e82a4ffcad6f6c7540688d3369aa6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72561283"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Come scrivere un manifesto del modulo PowerShell

Dopo aver scritto il modulo di PowerShell, è possibile aggiungere un manifesto del modulo facoltativo che include informazioni sul modulo. Ad esempio, è possibile descrivere l'autore, specificare i file nel modulo, ad esempio i moduli annidati, eseguire script per personalizzare l'ambiente dell'utente, caricare i file di tipo e di formattazione, definire i requisiti di sistema e limitare i membri esportati dal modulo.

## <a name="creating-a-module-manifest"></a>Creazione di un manifesto del modulo

Un **manifesto del modulo** è un file di dati di PowerShell (`.psd1`) che descrive il contenuto di un modulo e determina la modalità di elaborazione di un modulo. Il file manifesto è un file di testo che contiene una tabella hash di chiavi e valori. È possibile collegare un file manifesto a un modulo denominando il manifesto come il modulo e archiviando il manifesto nella directory radice del modulo.

Per i moduli semplici che contengono solo un singolo `.psm1` o un assembly binario, un manifesto del modulo è facoltativo. Tuttavia, si consiglia di usare un manifesto del modulo quando possibile, perché sono utili per organizzare il codice e mantenere le informazioni sul controllo delle versioni. Per esportare un assembly installato nella [global assembly cache](/dotnet/framework/app-domains/gac)è necessario un manifesto del modulo. Un manifesto del modulo è necessario anche per i moduli che supportano la funzionalità Guida aggiornabile. La guida aggiornabile usa la chiave **HelpInfoUri** nel manifesto del modulo per trovare il file di informazioni della guida (HELPINFO XML) che contiene il percorso dei file della Guida aggiornati per il modulo. Per ulteriori informazioni sulla guida aggiornabile, vedere Supporto per la [Guida aggiornabile](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Per creare e utilizzare un manifesto del modulo

1. La procedura consigliata per creare un manifesto del modulo consiste nell'usare il cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) . È possibile usare i parametri per specificare uno o più valori e chiavi predefinite del manifesto. L'unico requisito consiste nel denominare il file. `New-ModuleManifest` crea un manifesto del modulo con i valori specificati e include le chiavi rimanenti e i relativi valori predefiniti. Se è necessario creare più moduli, usare `New-ModuleManifest` per creare un modello di manifesto del modulo che può essere modificato per i diversi moduli. Per un esempio di manifesto del modulo predefinito, vedere il [manifesto del modulo di esempio](#sample-module-manifest).

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   In alternativa, è possibile creare manualmente la tabella hash del manifesto del modulo usando le informazioni minime necessarie, **ModuleVersion**. Salvare il file con lo stesso nome del modulo e usare l'estensione del file `.psd1`. È quindi possibile modificare il file e aggiungere le chiavi e i valori appropriati.

1. Aggiungere eventuali elementi aggiuntivi desiderati nel file manifesto.

   Per modificare il file manifesto, usare qualsiasi editor di testo preferito. Tuttavia, il file manifesto è un file di script che contiene il codice, pertanto può essere necessario modificarlo in un ambiente di scripting o di sviluppo, ad esempio Visual Studio Code. Tutti gli elementi di un file manifesto sono facoltativi, ad eccezione del numero **ModuleVersion** .

   Per le descrizioni delle chiavi e dei valori che è possibile includere in un manifesto del modulo, vedere la tabella [elementi manifesto del modulo](#module-manifest-elements) . Per ulteriori informazioni, vedere le descrizioni dei parametri nel cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) .

1. Per risolvere gli scenari che potrebbero non essere coperti dagli elementi manifesto del modulo di base, è possibile aggiungere altro codice al manifesto del modulo.

   Per motivi di sicurezza, PowerShell esegue solo un piccolo subset delle operazioni disponibili in un file manifesto del modulo. In genere, è possibile usare l'istruzione `if`, gli operatori aritmetici e di confronto e i tipi di dati di base di PowerShell.

1. Dopo aver creato il manifesto del modulo, è possibile testarlo per verificare che tutti i percorsi descritti nel manifesto siano corretti. Per testare il manifesto del modulo, usare [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

1. Assicurarsi che il manifesto del modulo si trovi nel primo livello della directory che contiene il modulo.

   Quando si copia il modulo su un sistema e lo si importa, PowerShell usa il manifesto del modulo per importare il modulo.

1. Facoltativamente, è possibile testare direttamente il manifesto del modulo con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) tramite il punto di sourcing del manifesto stesso.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementi del manifesto del modulo

Nella tabella seguente vengono descritti gli elementi che è possibile includere in un manifesto del modulo.

|Elemento|Valore predefinito|Description|
|-------------|-------------|-----------------|
|**RootModule**<br /> Tipo: `String`|`<empty string>`|File del modulo di script o del modulo binario associato a questo manifesto. Le versioni precedenti di PowerShell denominavano questo elemento **ModuleToProcess**.<br /> I tipi possibili per il modulo radice possono essere vuoti, che consente di creare un modulo **manifesto** , il nome di un modulo di script (`.psm1`) o il nome di un modulo binario (`.exe` o `.dll`). L'inserimento del nome di un manifesto del modulo (`.psd1`) o di un file di script (`.ps1`) in questo elemento causa un errore. <br /> Esempio: `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> Tipo: `Version`|`'0.0.1'`|Numero di versione del modulo. Se non si specifica un valore, `New-ModuleManifest` usa il valore predefinito. La stringa deve essere in grado di eseguire la conversione al tipo `Version` ad esempio `#.#.#.#.#`. `Import-Module` carica il primo modulo rilevato nell' **$PSModulePath** che corrisponde al nome e ha almeno un valore di **ModuleVersion**come parametro **MinimumVersion** . Per importare una versione specifica, usare il parametro **RequiredVersion** del cmdlet `Import-Module`.<br /> Esempio: `ModuleVersion = '1.0'`|
|**GUID**<br /> Tipo: `GUID`|`'<GUID>'`|ID usato per identificare in modo univoco il modulo. Se non si specifica un valore, `New-ModuleManifest` genera automaticamente il valore. Attualmente non è possibile importare un modulo per **GUID**. <br /> Esempio: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Autore**<br /> Tipo: `String`|`'<Current user>'`|Autore del modulo. Se non si specifica un valore, `New-ModuleManifest` utilizza l'utente corrente. <br /> Esempio: `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> Tipo: `String`|`'Unknown'`|Società o fornitore di questo modulo. Se non si specifica un valore, `New-ModuleManifest` usa il valore predefinito.<br /> Esempio: `CompanyName = 'Fabrikam'`|
|**Copyright**<br /> Tipo: `String`|`'(c) <Author>. All rights reserved.'`| Dichiarazione del copyright per questo modulo. Se non si specifica un valore, `New-ModuleManifest` utilizza l'impostazione predefinita con l'utente corrente come `<Author>`. Per specificare un autore, usare il parametro **Author** . <br /> Esempio: `Copyright = '2019 AuthorName. All rights reserved.'`|
|**Descrizione**<br /> Tipo: `String`|`<empty string>`|Descrizione della funzionalità fornita da questo modulo.<br /> Esempio: `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> Tipo: `Version`|`<empty string>`|Versione minima del motore di PowerShell richiesta da questo modulo. I valori validi sono 1,0, 2,0, 3,0, 4,0, 5,0, 5,1, 6 e 7.<br /> Esempio: `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> Tipo: `String`|`<empty string>`|Nome dell'host PowerShell richiesto da questo modulo. Questo nome viene fornito da PowerShell. Per trovare il nome di un programma host, nel programma digitare: `$host.name`.<br /> Esempio: `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> Tipo: `Version`|`<empty string>`|Versione minima dell'host PowerShell richiesta da questo modulo.<br /> Esempio: `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> Tipo: `Version`|`<empty string>`|Versione minima di Microsoft .NET Framework richiesta da questo modulo. Questo prerequisito è valido solo per l'edizione desktop di PowerShell, ad esempio PowerShell 5,1.<br /> Esempio: `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> Tipo: `Version`|`<empty string>`|Versione minima del Common Language Runtime (CLR) richiesta da questo modulo. Questo prerequisito è valido solo per l'edizione desktop di PowerShell, ad esempio PowerShell 5,1.<br /> Esempio: `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> Tipo: `ProcessorArchitecture`|`<empty string>`|Architettura del processore (nessuno, x86, amd64) richiesta da questo modulo. I valori validi sono x86, AMD64, ARM, IA64, MSIL e nessuno (sconosciuto o non specificato).<br /> Esempio: `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> Tipo: `Object[]`|`@()`|Moduli che devono essere importati nell'ambiente globale prima di importare il modulo. Verranno caricati tutti i moduli elencati a meno che non siano già stati caricati. Ad esempio alcuni moduli potrebbero essere già stati caricati da un modulo diverso. È possibile specificare una versione specifica da caricare utilizzando `RequiredVersion` anziché `ModuleVersion`. Quando si utilizza `ModuleVersion`, viene caricata la versione più recente disponibile con almeno la versione specificata. È possibile combinare stringhe e tabelle hash nel valore del parametro.<br /> Esempio: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> Esempio: `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> Tipo: `String[]`|`@()`|Assembly che devono essere caricati prima di importare il modulo. Specifica i nomi di file di assembly (`.dll`) richiesti dal modulo.<br /> PowerShell carica gli assembly specificati prima di aggiornare tipi o formati, importare moduli nidificati o importare il file di modulo specificato nel valore della chiave RootModule. Usare questo parametro per elencare tutti gli assembly richiesti dal modulo.<br /> Esempio: `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> Tipo: `String[]`|`@()`|Script (`.ps1`) file che vengono eseguiti nello stato sessione del chiamante quando viene importato il modulo. Potrebbe trattarsi dello stato della sessione globale o, per i moduli nidificati, dello stato della sessione di un altro modulo. È possibile usare questi script per preparare un ambiente Analogamente a come si può usare uno script di accesso.<br /> Questi script vengono eseguiti prima del caricamento di uno dei moduli elencati nel manifesto. <br /> Esempio: `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> Tipo: `String[]`|`@()`|Digitare i file (`.ps1xml`) da caricare durante l'importazione del modulo. <br /> Esempio: `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> Tipo: `String[]`|`@()`|File di formato (`.ps1xml`) da caricare durante l'importazione del modulo. <br /> Esempio: `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> Tipo: `Object[]`|`@()`|Moduli da importare come moduli annidati del modulo specificato in **RootModule** (alias:**ModuleToProcess**).<br /> L'aggiunta di un nome di modulo a questo elemento è simile alla chiamata di `Import-Module` dall'interno dello script o del codice dell'assembly. La differenza principale con un file manifesto è che è più semplice vedere ciò che si sta caricando. Se il caricamento di un modulo non riesce, non sarà ancora stato caricato il modulo effettivo.<br /> Oltre ad altri moduli, è anche possibile caricare i file di script (`.ps1`) qui. Questi file vengono eseguiti nel contesto del modulo radice. Equivale a punteggiare lo script nel modulo radice. <br /> Esempio: `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> Tipo: `String[]`|`@()`|Specifica le funzioni da esportare da questo modulo, per ottenere prestazioni ottimali, non utilizzare caratteri jolly e non eliminare la voce, utilizzare una matrice vuota se non sono presenti funzioni da esportare. Per impostazione predefinita, non viene esportata alcuna funzione. È possibile usare questa chiave per elencare le funzioni esportate dal modulo.<br /> Il modulo Esporta le funzioni nello stato sessione del chiamante. Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutte le funzioni esportate da un modulo annidato verranno esportate nello stato sessione globale, a meno che un modulo nella catena non limiti la funzione tramite la chiave **FunctionsToExport** .<br /> Se il manifesto Esporta alias per le funzioni, questa chiave può rimuovere le funzioni i cui alias sono elencate nella chiave **AliasesToExport** , ma questa chiave non può aggiungere alias di funzione all'elenco. <br /> Esempio: `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> Tipo: `String[]`|`@()`|Specifica i cmdlet da esportare da questo modulo, per ottenere prestazioni ottimali, non utilizzare caratteri jolly e non eliminare la voce, utilizzare una matrice vuota se non sono presenti cmdlet da esportare. Per impostazione predefinita, non viene esportato alcun cmdlet. È possibile usare questa chiave per elencare i cmdlet che vengono esportati dal modulo.<br /> Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutti i cmdlet esportati da un modulo annidato verranno esportati nello stato sessione globale, a meno che un modulo nella catena non limiti il cmdlet tramite la chiave **CmdletsToExport** .<br /> Se il manifesto Esporta alias per i cmdlet, questa chiave può rimuovere i cmdlet i cui alias sono elencati nella chiave **AliasesToExport** , ma questa chiave non può aggiungere alias di cmdlet all'elenco. <br /> Esempio: `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> Tipo: `String[]`|`'*'`|Specifica le variabili esportate dal modulo nello stato sessione del chiamante. I caratteri jolly sono consentiti. Per impostazione predefinita, vengono esportate tutte le variabili (`'*'`). È possibile usare questa chiave per limitare le variabili esportate dal modulo.<br /> Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutte le variabili esportate da un modulo annidato verranno esportate nello stato sessione globale, a meno che un modulo nella catena non limiti la variabile utilizzando la chiave **VariablesToExport** .<br /> Se il manifesto esporta anche alias per le variabili, questa chiave può rimuovere le variabili i cui alias sono elencati nella chiave **AliasesToExport** , ma questa chiave non può aggiungere alias di variabile all'elenco. <br /> Esempio: `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> Tipo: `String[]`|`@()`|Specifica gli alias da esportare da questo modulo. per ottenere prestazioni ottimali, non utilizzare caratteri jolly e non eliminare la voce, utilizzare una matrice vuota se non sono presenti alias da esportare. Per impostazione predefinita, non viene esportato alcun alias. È possibile usare questa chiave per elencare gli alias esportati dal modulo.<br /> Il modulo Esporta gli alias nello stato sessione del chiamante. Lo stato della sessione del chiamante può essere lo stato della sessione globale o, per i moduli nidificati, lo stato della sessione di un altro modulo. Quando si concatenano i moduli annidati, tutti gli alias esportati da un modulo annidato verranno infine esportati nello stato sessione globale, a meno che un modulo nella catena non limiti l'alias tramite la chiave **AliasesToExport** . <br /> Esempio: `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> Tipo: `String[]`|`@()`|Specifica le risorse DSC da esportare da questo modulo. I caratteri jolly sono consentiti. <br /> Esempio: `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**Modulo di**<br /> Tipo: `Object[]`|`@()`|Specifica tutti i moduli inclusi in un pacchetto con questo modulo. Questi moduli possono essere immessi in base al nome, usando una stringa delimitata da virgole o come tabella hash con le chiavi **ModuleName** e **GUID** . La tabella hash può anche avere una chiave **ModuleVersion** facoltativa. La chiave del **modulo** è progettata per fungere da inventario dei moduli. Questi moduli non vengono elaborati automaticamente. <br /> Esempio: `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList**<br /> Tipo: `String[]`|`@()`|Elenco di tutti i file inclusi in questo modulo. Come con l'elenco di **moduli**, filelist è un elenco di inventario e **non viene elaborato** in altro modo. <br /> Esempio: `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> Tipo: `Object`|`@{...}`|Specifica i dati privati che devono essere passati al modulo radice specificato dalla chiave **RootModule** (alias: **ModuleToProcess**). **PrivateData** è una tabella hash che comprende diversi elementi: **Tags**, **LicenseUri**, **ProjectURI**, **iconUri**, **releasenotes**, **prerelease**, **RequireLicenseAcceptance**e **ExternalModuleDependencies**. |
|**Tag** <br /> Tipo: `String[]` |`@()`| Consente di contrassegnare l'individuazione dei moduli nelle raccolte online. <br /> Esempio: `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> Tipo: `Uri` |`<empty string>`| URL della licenza per il modulo. <br /> Esempio: `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> Tipo: `Uri` |`<empty string>`| URL del sito Web principale per il progetto. <br /> Esempio: `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> Tipo: `Uri` |`<empty string>`| URL di un'icona che rappresenta questo modulo. <br /> Esempio: `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> Tipo: `String` |`<empty string>`| Specifica le note sulla versione del modulo. <br /> Esempio: `ReleaseNotes = 'The release notes provide information about the module.`|
|**PreRelease**<br /> Tipo: `String` |`<empty string>`| Questo parametro è stato aggiunto in PowerShell 7. Una stringa **provvisoria** che identifica il modulo come versione non definitiva nelle raccolte online. <br /> Esempio: `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> Tipo: `Boolean`|`$true`| Questo parametro è stato aggiunto in PowerShell 7. Flag che indica se il modulo richiede l'accettazione esplicita dell'utente per l'installazione, l'aggiornamento o il salvataggio. <br /> Esempio: `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> Tipo: `String[]` |`@()`| Questo parametro è stato aggiunto in PowerShell 7. Elenco di moduli esterni da cui dipende questo modulo. <br /> Esempio: `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> Tipo: `String`|`<empty string>`|URI HelpInfo del modulo. <br /> Esempio: `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> Tipo: `String`|`<empty string>`|Prefisso predefinito per i comandi esportati da questo modulo. Eseguire l'override del prefisso predefinito utilizzando `Import-Module -Prefix`. <br /> Esempio: `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>Manifesto del modulo di esempio

Il manifesto del modulo di esempio seguente è stato creato con `New-ModuleManifest` in PowerShell 7 e contiene le chiavi e i valori predefiniti.

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
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

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>Vedere anche

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[Global Assembly Cache](/dotnet/framework/app-domains/gac)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
