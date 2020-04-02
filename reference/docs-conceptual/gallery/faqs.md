---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Domande frequenti su PowerShell Gallery
ms.openlocfilehash: 035681e108e1a3e05fe5d659d527ae1ad1c64cf4
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500579"
---
# <a name="frequently-asked-questions"></a>Domande frequenti

## <a name="what-is-a-powershell-module"></a>Che cos'è un modulo di PowerShell?

Un modulo di PowerShell è un pacchetto riutilizzabile che contiene alcune funzionalità di PowerShell. Tutti gli elementi di PowerShell, ad esempio funzioni, variabili, risorse DSC e così via, possono essere inseriti nei moduli. In genere, i moduli sono cartelle che contengono determinati tipi di file archiviati in un percorso specifico. Sono disponibili diversi tipi di moduli di PowerShell.

## <a name="what-is-a-powershell-script"></a>Che cos'è uno script di PowerShell?

Uno script di PowerShell è composto da una serie di comandi che vengono archiviati in un file ps1 per abilitare il riutilizzo e la condivisione. Anche i flussi di lavoro di PowerShell sono script di PowerShell che descrivono e stabiliscono la sequenza di un set di attività. Per altre informazioni, visitare [Informazioni sul flusso di lavoro di Windows PowerShell](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Quali sono le differenze tra gli script e i moduli di PowerShell?

In generale, i moduli sono più adatti per la condivisione. Tuttavia, Microsoft sta abilitando la condivisione degli script per rendere più semplice la collaborazione sui flussi di lavoro e gli script nella community. Per altre informazioni, vedere i blog seguenti:

- [Don't Write Scripts, Write PowerShell Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/) (Non scrivere script, ma moduli di PowerShell)
- [Understanding PowerShell Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/) (Informazioni sui moduli di PowerShell)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Come si pubblica in PowerShell Gallery?

Per pubblicare i pacchetti nella raccolta, è prima necessario registrare un account in PowerShell Gallery perché la pubblicazione di pacchetti richiede una chiave NuGetApiKey, fornita al momento della registrazione. Per registrarsi, usare l'account personale, aziendale o dell'istituto di istruzione per poter accedere a PowerShell Gallery. Quando si accede per la prima volta, è necessario un processo di registrazione una tantum.
Successivamente, la chiave NuGetApiKey sarà disponibile nella pagina del profilo.

Dopo la registrazione in PowerShell Gallery, usare i cmdlet [Publish-Module][] o [Publish-Script][] per pubblicare il pacchetto nella raccolta. Per altre informazioni dettagliate su come eseguire questi cmdlet, andare alla scheda Publish (Pubblica) o leggere la documentazione su [Publish-Module][] e [Publish-Script][].

**Non è necessario registrarsi o accedere a PowerShell Gallery per installare o salvare i pacchetti.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Viene visualizzato l'errore di mancata elaborazione della richiesta, causato dalla chiave API che non è valida o non ha le autorizzazioni per accedere al pacchetto specificato. Errore del server remoto: (403) Non consentito." quando si prova a pubblicare un pacchetto in PowerShell Gallery. Che cosa significa?

Le cause di questo errore sono le seguenti:

- **La chiave API specificata non è valida.** Verificare di aver specificato una chiave API valida nell'account. Per ottenere la chiave API, visualizzare la pagina del profilo.
- **Il nome del pacchetto specificato non è di proprietà dell'utente.** Se si è verificato che la chiave API è corretta, potrebbe essere già presente un pacchetto con lo stesso nome di quello che si sta provando a usare. Il pacchetto potrebbe essere stato escluso dall'elenco dal proprietario, di conseguenza non viene visualizzato nei risultati di ricerca. Per determinare se esiste già un pacchetto con lo stesso nome, aprire un browser e passare alla pagina dei dettagli del pacchetto: `https://www.powershellgallery.com/packages/<packageName>`. Ad esempio, se si passa direttamente a `https://www.powershellgallery.com/packages/pester`, viene visualizzata la pagina dei dettagli del modulo Pester, a prescindere che sia incluso o meno nell'elenco. Se esiste già un pacchetto con un nome in conflitto e non si trova nell'elenco, è possibile:
  - Selezionare un altro nome per il pacchetto.
  - Contattare i proprietari del pacchetto esistente.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Perché non riesco ad accedere con l'account personale che ieri funzionava?

Tenere presente che l'account della raccolta non consente di apportare modifiche all'alias di posta elettronica principale.
Per altre informazioni, vedere [Gestire gli alias per l'account Microsoft](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Perché non sono visualizzati tutti i pacchetti della raccolta quando si selezionano tutte le caselle di controllo Category (Categoria) nella scheda Packages (Pacchetti)?

Quando si seleziona una casella di controllo Category (Categoria), implicitamente si richiede di visualizzare tutti i pacchetti presenti nella categoria specificata, quindi vengono mostrati solo i pacchetti nelle categorie selezionate. Analogamente, quando si selezionano tutte le caselle di controllo Category (Categoria), implicitamente si richiede di visualizzare tutti i pacchetti presenti in qualsiasi categoria. Alcuni pacchetti nella raccolta, tuttavia, non appartengono ad alcuna delle categorie elencate, quindi non verranno visualizzati nei risultati. Per visualizzare tutti i pacchetti in PowerShell Gallery, deselezionare tutte le categorie o selezionare di nuovo la scheda Packages (Pacchetti).

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Quali sono i requisiti per la pubblicazione di un modulo in PowerShell Gallery?

Qualsiasi tipo di modulo di PowerShell, inclusi i moduli di script, i moduli binari e i moduli del manifesto, può essere pubblicato nella raccolta. Per pubblicare un modulo, PowerShellGet deve avere alcune informazioni, ovvero la versione, la descrizione, l'autore e la modalità di licenza. Queste informazioni vengono lette nell'ambito del processo di pubblicazione dal file *manifesto del modulo* (con estensione psd1) o nel valore del parametro **LicenseUri** del cmdlet [Publish-Module][]. Tutti i moduli pubblicati nella raccolta devono includere manifesti dei moduli. Tutti i moduli che includono le informazioni seguenti nei propri manifesti possono essere pubblicati nella raccolta:

- Versione
- Descrizione
- Autore
- URI per le condizioni di licenza del modulo, come parte della sezione **PrivateData** del manifesto o nel parametro **LicenseUri** del cmdlet [Publish-Module][].

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Come si crea un manifesto del modulo formattato correttamente?

Il modo più semplice per creare un manifesto del modulo consiste nell'eseguire il cmdlet [New-ModuleManifest][]. In PowerShell 5.0 o versioni successive New-ModuleManifest genera un manifesto del modulo formattato correttamente con i campi vuoti per i metadati utili come **ProjectUri**, **LicenseUri** e **Tag**. È sufficiente compilare i campi vuoti o usare il manifesto generato come esempio di formattazione corretta.

Per verificare che tutti i campi di metadati richiesti siano compilati correttamente, usare il cmdlet [Test-ModuleManifest][].

Per aggiornare i campi del file manifesto del modulo, usare il cmdlet [Update-ModuleManifest][].

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Quali sono i requisiti per la pubblicazione di uno script nella raccolta?

Nella raccolta può essere pubblicato qualsiasi tipo di script PowerShell, sia script che flussi di lavoro. Per pubblicare uno script, PowerShellGet deve avere alcune informazioni, ovvero la versione, la descrizione, l'autore e la modalità di licenza. Queste informazioni vengono lette nell'ambito del processo di pubblicazione dalla sezione *PSScriptInfo* del file di script o dal valore del parametro **LicenseUri** del cmdlet [Publish-Script][]. Tutti gli script pubblicati nella raccolta devono includere informazioni sui metadati. Tutti gli script che includono le informazioni seguenti nella sezione PSScriptInfo possono essere pubblicati nella raccolta:

- Versione
- Descrizione
- Autore
- URI per le condizioni di licenza dello script, come parte della sezione **PSScriptInfo** dello script o nel parametro **LicenseUri** del cmdlet [Publish-Script][].

## <a name="how-do-i-search"></a>Come si esegue la ricerca?

Digitare ciò che si sta cercando nella casella di testo. Ad esempio, per trovare i moduli correlati a SQL di Azure, digitare "azure sql". Il motore di ricerca cerca le parole chiave in tutti i pacchetti pubblicati, inclusi i titoli, le descrizioni e i metadati. Quindi, in base a un punteggio di qualità ponderata, visualizza le corrispondenze più vicine. È anche possibile cercare un campo specifico, usando la sintassi field:"value" nella query di ricerca per i campi seguenti:

- Tag
- Funzioni
- Cmdlet
- DscResources
- PowerShellVersion

Ad esempio, quando si cerca PowerShellVersion: "2.0", vengono visualizzati solo i risultati compatibili con PowerShellVersion 2.0, in base al manifesto di modulo o script.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Come si crea un file di script formattato correttamente?

Il modo più semplice per creare un file di script formattato correttamente consiste nell'eseguire il cmdlet [New-ScriptFileInfo][]. In PowerShell 5.0 New-ScriptFileInfo genera un file di script formattato correttamente con i campi vuoti per i metadati utili come **ProjectUri**, **LicenseUri** e **Tag**. È sufficiente compilare i campi vuoti o usare il file di script generato come esempio di formattazione corretta.

Per verificare che tutti i campi di metadati richiesti siano compilati correttamente, usare il cmdlet [Test-ScriptFileInfo][].

Per aggiornare i campi dei metadati di script, usare il cmdlet [Update-ScriptFileInfo][].

## <a name="what-other-types-of-powershell-modules-exist"></a>Quali altri tipi di moduli di PowerShell esistono?

Il termine modulo di PowerShell fa riferimento anche ai file che implementano funzionalità effettive. I file del modulo di script (con estensione psm1) contengono codice PowerShell. I file del modulo binario (DLL) contengono codice compilato.

In altre parole, la cartella che incapsula il modulo è la cartella del modulo. La cartella del modulo può contenere un manifesto del modulo (con estensione psd1) che descrive il contenuto della cartella. I file che eseguono effettivamente l'operazione sono i file del modulo di script (psm1) e i file del modulo binario (DLL). Le risorse DSC si trovano in una sottocartella specifica e vengono implementate come file del modulo di script o file del modulo binario.

Tutti i moduli nella raccolta contengono manifesti dei moduli e la maggior parte di questi moduli contiene file del modulo di script o file del modulo binario. Il termine "modulo" può generare confusione a causa di questi diversi significati. Se non specificato diversamente, tutti gli usi della parola "modulo" in questa pagina fanno riferimento alla cartella del modulo che contiene questi file.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Qual è la relazione tra PackageManagement e PowerShellGet? (Risposta di alto livello)

PackageManagement è un'interfaccia comune per l'utilizzo di qualsiasi strumento di gestione dei pacchetti. Se si usano moduli di PowerShell, file MSI, Ruby Gems, pacchetti NuGet o moduli Perl, si dovrebbero poter usare i comandi di PackageManagement, ovvero Find-Package e Install-Package, per trovarli e installarli. A tale scopo, PackageManagement usa un provider di pacchetti per ogni strumento di gestione dei pacchetti collegato a PackageManagement. I provider eseguono tutte le operazioni effettive: recuperano il contenuto dai repository e installano il contenuto localmente. Spesso, i provider di pacchetti eseguono semplicemente il wrapping degli strumenti di gestione dei pacchetti esistenti per un determinato tipo di pacchetto.

PowerShellGet è lo strumento di gestione dei pacchetti per i pacchetti di PowerShell. Esiste un provider di pacchetti PSModule che espone la funzionalità PowerShellGet con PackageManagement. Per questo motivo, è possibile eseguire [Install-Module][] o Install-Package-Provider PSModule per installare un modulo da PowerShell Gallery. L'accesso ad alcune funzionalità di PowerShellGet, incluse [Update-Module][] e [Publish-Module][], non può essere eseguito con i comandi di PackageManagement.

In sintesi, PowerShellGet è incentrato esclusivamente sull'esperienza di gestione dei pacchetti premium per il contenuto di PowerShell. PackageManagement si concentra sull'esposizione di tutte le esperienze di gestione dei pacchetti con un set generale di strumenti. Se questa risposta non è soddisfacente, è disponibile una risposta più completa alla fine di questo documento, nella sezione **Qual è la modalità effettiva di relazione tra PackageManagement e PowerShellGet?** .

Per altre informazioni, visitare la [pagina del progetto PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Qual è la relazione tra NuGet e PowerShellGet?

PowerShell Gallery è una versione modificata di [NuGet Gallery](https://www.nuget.org/).
PowerShellGet usa il provider NuGet per lavorare con i repository basati su NuGet come PowerShell Gallery.

È possibile usare PowerShellGet con qualsiasi repository NuGet o condivisione di file valida. È sufficiente aggiungere il repository eseguendo il cmdlet [Register-PSRepository][].

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Significa che è possibile usare NuGet.exe per lavorare con la raccolta?

Sì.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Qual è la modalità effettiva di relazione tra PackageManagement e PowerShellGet? (Dettagli tecnici)

Dietro le quinte, PowerShellGet sfrutta in modo intensivo l'infrastruttura di PackageManagement.

Al livello dei cmdlet di PowerShell, [Install-Module][] è un semplice wrapper per `Install-Package -Provider PSModule`.

Al livello dei provider di pacchetti PackageManagement, il provider di pacchetti PSModule esegue una chiamata negli altri provider di pacchetti PackageManagement. Ad esempio, quando si lavora con le raccolte basate su NuGet (ad esempio la PowerShell Gallery), il provider di pacchetti PSModule usa il provider del pacchetto NuGet per lavorare con il repository.

![Architettura di PowerShellGet](media/faqs/powershellgetArchitecture.png)

Figura 1: Architettura di PowerShellGet

## <a name="what-is-required-to-run-powershellget"></a>Quali sono i requisiti per l'esecuzione di PowerShellGet?

In generale si consiglia di scegliere la versione più recente del modulo PowerShellGet. È necessario .NET 4.5.

Il modulo **PowerShellGet** richiede **PowerShell 3.0 o versione successiva**.

Di conseguenza, **PowerShellGet** richiede uno dei sistemi operativi seguenti:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** richiede anche .NET Framework 4.5 o versione successiva. È possibile installare .NET Framework 4.5 o versione successiva da [qui](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>È possibile riservare i nomi per pacchetti che verranno pubblicati in futuro?

Non è possibile prenotare i nomi dei pacchetti. Se si ritiene che il nome di un pacchetto esistente sia più appropriato per il proprio pacchetto, provare a [contattare il proprietario del pacchetto](./how-to/working-with-packages/contacting-package-owners.md).
Se si non ottiene risposta entro un paio di settimane, è possibile contattare il supporto e il team di PowerShell Gallery analizzerà il problema.

## <a name="how-do-i-claim-ownership-for-packages"></a>Come è possibile richiedere la proprietà per i pacchetti?

Per informazioni dettagliate, vedere [Gestione dei proprietari di pacchetti](./how-to/publishing-packages/managing-package-owners.md).

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Come è possibile gestire il caso in cui il proprietario di un pacchetto viola la licenza del pacchetto di un altro utente?

Si consiglia alla community di PowerShell di collaborare per risolvere i conflitti che possono verificarsi tra i proprietari di un pacchetto e i proprietari di altri pacchetti. È stato predisposto un [processo di risoluzione delle controversie](./how-to/getting-support/dispute-resolution.md) che verrà richiesto di seguire prima che intervengano gli amministratori di PowerShellGallery.com.

<!-- link references-->
[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/PowerShellGet/Update-ModuleManifest
[Install-Module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publish-Module]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
