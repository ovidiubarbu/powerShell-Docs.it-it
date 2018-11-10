---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
description: Linee guida per gli autori
title: Linee guida e procedure consigliate per la pubblicazione in PowerShell Gallery
ms.openlocfilehash: 7e9eca8d3372ddf0b94ab42e125991b857456551
ms.sourcegitcommit: aa1129cc2b0ae6e18918b2b0ea70c74915ed019b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50235406"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Linee guida e procedure consigliate per la pubblicazione in PowerShell Gallery

Questo argomento descrive le procedure consigliate usate dai team Microsoft per garantire che i pacchetti pubblicati in PowerShell Gallery vengano adottati in modo estensivo e offrano valore aggiunto agli utenti. Le procedure consigliate si basano sulle modalità di gestione dei dati del manifesto in PowerShell Gallery e sui commenti e suggerimenti di numerosi utenti di PowerShell Gallery.
I pacchetti pubblicati attenendosi a queste linee guida hanno maggiori probabilità di essere installati e considerati attendibili e attraggono un numero maggiore di utenti.

Di seguito sono elencate le linee guida che definiscono un pacchetto di PowerShell Gallery di qualità, le impostazioni facoltative più importanti di un manifesto e suggerimenti per migliorare il codice con i commenti e i suggerimenti dei revisori iniziali e con [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer). Inoltre sono incluse linee guida per creare versioni del modulo, documentazione, test ed esempi per l'uso degli elementi condivisi.
Questa documentazione segue in gran parte le linee guida per la pubblicazione di [moduli risorsa DSC di qualità](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Per informazioni sulle modalità di pubblicazione di un pacchetto in PowerShell Gallery vedere [Creazione e pubblicazione di un pacchetto](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Sono graditi i commenti e i suggerimenti relativi a queste linee guida. Per pubblicare osservazioni è possibile aprire un caso nell'[archivio della documentazione Github](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Procedure consigliate per la pubblicazione di pacchetti

Le seguenti procedure consigliate sono state segnalate come importanti dagli utenti degli elementi di PowerShell Gallery e sono elencate in ordine di priorità nominale.
I pacchetti creati usando queste linee guida hanno molte più probabilità di essere scaricati e adottati da altri utenti.

- Usare PSScriptAnalyzer
- Includere documentazione ed esempi
- Rispondere a commenti e suggerimenti
- Includere moduli anziché script
- Includere un collegamento a un sito di progetto
- Includere test con i moduli
- Includere e/o collegare condizioni di licenza
- Firmare il codice
- Osservare le linee guida [SemVer](http://semver.org/) per il controllo delle versioni
- Usare tag comuni, documentati nei tag comuni di PowerShell Gallery
- Pubblicazione di test usando un repository locale
- Usare PowerShellGet per la pubblicazione

Ogni voce viene descritta brevemente nelle sezioni che seguono.

## <a name="use-psscriptanalyzer"></a>Usare PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) è uno strumento di analisi del codice statico gratuito che funziona con il codice PowerShell.
PSScriptAnalyzer identifica i problemi più comuni del codice di PowerShell e in molti casi offre un suggerimento per la risoluzione.
Lo strumento è facile da usare e classifica i problemi come Error (Errore, problema grave che deve essere risolto), Warning (Avviso, problema che va esaminato e dovrebbe essere risolto) e Information (Informazione, problema da esaminare per la conformità alle procedure consigliate).
Tutti i pacchetti pubblicati in PowerShell Gallery vengono esaminati con PSScriptAnalyzer e gli eventuali errori vengono restituiti al proprietario e devono essere risolti.

La procedura consigliata consiste nell'eseguire `Invoke-ScriptAnalyzer` con `-Recurse` e `-Severity` impostata su Warning (Avviso).

Esaminare i risultati e verificare quanto segue:

- Tutti i problemi di tipo Error sono stati corretti o sono illustrati nella documentazione.
- Tutti i problemi di tipo Warning sono stati esaminati e risolti se necessario.

Per gli utenti che acquisiscono pacchetti di PowerShell Gallery è vivamente consigliabile l'esecuzione di PSScriptAnalyzer e l'esame di tutti i problemi di tipo Error e Warning.
Se un utente nota che PSScriptAnalyzer segnala un errore è molto probabile che tenti di contattare il proprietario del pacchetto corrispondente.
Se esiste un motivo fondato per mantenere nel pacchetto codice che viene segnalato come errore, aggiungere le informazioni corrispondenti alla documentazione, per evitare di dover rispondere molte volte alla stessa domanda.

## <a name="include-documentation-and-examples"></a>Includere documentazione ed esempi

La documentazione e gli esempi sono il metodo migliore per consentire agli utenti di trarre il massimo vantaggio dal codice condiviso.

La documentazione è l'elemento più importante da includere nei pacchetti pubblicati in PowerShell Gallery.
In genere gli utenti ignorano i pacchetti privi di documentazione, perché dovrebbero leggere direttamente il codice per capire che cos'è il pacchetto e come va usato.
Sono disponibili vari articoli che illustrano come includere documentazione con i pacchetti di PowerShell, tra cui:

- Suggerimenti per la creazione della documentazione sono disponibili in [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Come scrivere documentazione per i cmdlet).
- La creazione di documentazione per i cmdlet è l'approccio migliore per script, funzioni o cmdlet di PowerShell.
  Per informazioni su come creare la Guida per i cmdlet, iniziare da [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Come scrivere la Guida per i cmdlet).
  Per aggiungere elementi di documentazione in uno script vedere [About Comment Based Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) (Informazioni sulla documentazione basata sui commenti).
- Molti moduli includono anche documentazione in formato testo, ad esempio file Markdown.
  Questa soluzione può essere utile se è disponibile un sito del progetto in Github, dove Markdown è un formato molto usato.
  La procedura consigliata è l'uso di [Markdown per Github](https://help.github.com/categories/writing-on-github/)

Gli esempi indicano agli utenti come usare il pacchetto.
Secondo molti sviluppatori, per capire come usare un elemento è utile vedere gli esempi prima della documentazione.
I migliori esempi indicano il funzionamento di base e un caso d'uso simulato realistico e includono commenti dettagliati al codice.
Gli esempi per i moduli pubblicati in PowerShell Gallery dovrebbero essere inclusi in una cartella Examples sotto la cartella radice del modulo.

Un modello ottimale per gli esempi è disponibile nel [modulo PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) nella cartella Examples\RegistryResource.
All'inizio di ogni file sono presenti quattro casi d'uso di esempio, corredati da una breve descrizione.

## <a name="respond-to-feedback"></a>Rispondere a commenti e suggerimenti

La community valuta positivamente i proprietari di pacchetti che offrono risposte adeguate a commenti e suggerimenti.
È importante rispondere agli utenti che offrono commenti e suggerimenti costruttivi, perché tali utenti sono interessati al pacchetto e cercano di migliorarlo.

In PowerShell Gallery sono disponibili due metodi per aggiungere commenti e suggerimenti:

- Contact Owner (Contatta il proprietario): l'utente può inviare un messaggio di posta elettronica al o ai proprietari del pacchetto. È importante che il proprietario del pacchetto controlli l'indirizzo di posta elettronica specificato con i pacchetti di PowerShell Gallery e risponda alle segnalazioni. L'unico svantaggio di questo metodo è il fatto che solo l'utente e il proprietario visualizzano questa comunicazione, pertanto è possibile che il proprietario debba rispondere molte volte alla stessa domanda.
- Comments (Commenti): nella parte inferiore della pagina del pacchetto è disponibile un campo Comment (Commento).
  Il vantaggio di questa opzione è il fatto che altri utenti possono vedere i commenti e le risposte, pertanto è necessario rispondere alla stessa domanda per un numero minore di volte.
  È consigliabile che il proprietario di un pacchetto segua i commenti aggiunti per ogni pacchetto.
Per informazioni su come procedere, vedere [Pubblicazione di feedback sui social media o nei commenti](../how-to/working-with-packages/social-media-feedback.md).

I proprietari che rispondono ai commenti e suggerimenti in modo costruttivo sono apprezzati dalla community.
Il report offre l'opportunità di richiedere altre informazioni, garantire una soluzione alternativa o specificare se un aggiornamento risolve un determinato problema.

Se in uno di questi due canali si rilevano comportamenti non appropriati, usare la funzionalità Segnala abusi di PowerShell Gallery per contattare gli amministratori della Gallery.

## <a name="modules-versus-scripts"></a>Moduli e script

La condivisione di uno script è molto utile e offre agli altri utenti esempi per la risoluzione di eventuali problemi riscontrati.
Tuttavia in PowerShell Gallery gli script sono file singoli senza documentazione, esempi e test separati.

I moduli di PowerShell hanno una struttura a cartelle che consente di includere più cartelle e file nel pacchetto.
La struttura del modulo consente l'inclusione degli altri pacchetti segnalati nelle procedure consigliate: guida dei cmdlet, documentazione, esempi e test.
Lo svantaggio principale è che uno script all'interno di un modulo deve essere presentato e usato come una funzione.
Per informazioni su come creare un modulo, vedere [Writing a Windows PowerShell Module](http://go.microsoft.com/fwlink/?LinkId=144916) (Scrittura di un modulo Windows PowerShell).

In determinate situazioni, ad esempio con le configurazioni DSC, uno script risulta più pratico per l'utente.
La procedura consigliata per le configurazioni DSC è la pubblicazione della configurazione come script con un modulo associato che contiene la documentazione, gli esempi e i test.
Lo script elenca il modulo associato usando RequiredModules = @(Nome del modulo).
Questo approccio può essere usato con qualsiasi script.

Gli script autonomi che seguono le altre procedure consigliate risultano comunque molto utili agli altri utenti.
La fornitura di documentazione basata sui commenti e del collegamento a un sito di progetto sono vivamente consigliate per la pubblicazione di uno script in PowerShell Gallery.

## <a name="provide-a-link-to-a-project-site"></a>Includere un collegamento a un sito di progetto

Nel sito di progetto l'autore può interagire direttamente con gli utenti dei pacchetti di PowerShell Gallery.
Gli utenti danno la preferenza ai pacchetti che includono un sito di progetto, in quanto consente di ottenere informazioni più facilmente.
Molti pacchetti in PowerShell Gallery sono sviluppati in GitHub, altri sono resi disponibili da organizzazioni con una presenza Web dedicata.
Entrambi gli ambienti possono essere considerati siti di progetto.

È possibile aggiungere un collegamento includendo ProjectURI nella sezione PSData del manifesto come indicato di seguito:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Quando viene specificato un ProjectURI, PowerShell Gallery include un collegamento al sito di progetto sul lato sinistro della pagina del pacchetto.

## <a name="include-tests"></a>Includere test

L'inclusione di test con il codice open source è importante per gli utenti, in quanto garantisce la convalida del codice e specifica informazioni sul suo funzionamento. Inoltre garantisce agli utenti la possibilità di adattare il codice al loro ambiente senza compromettere la funzionalità originale del codice stesso.

È consigliabile creare test che supportano il framework Pester, sviluppato espressamente per PowerShell.
Pester è disponibile in [GitHub](https://github.com/Pester/Pester), in [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/) ed è incluso in Windows 10, Windows Server 2016, WMF 5.0 e WMF 5.1.

Il [sito di progetto Pester in GitHub](https://github.com/Pester/Pester) include documentazione utile per la creazione di test Pester, dalle fasi iniziali alle procedure consigliate.

Gli obiettivi di code coverage dei test sono indicate nella [documentazione per la creazione di un modulo di risorse di qualità elevata](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md). Il valore di code coverage consigliato per lo unit test è 70%.

## <a name="include-andor-link-to-license-terms"></a>Includere e/o collegare condizioni di licenza

Tutti i pacchetti pubblicati in PowerShell Gallery devono specificare le condizioni di licenza o essere vincolati dalla licenza inclusa nelle [condizioni d'uso](https://www.powershellgallery.com/policies/Terms) alla voce "Exhibit A" (Allegato A).
L'approccio migliore per specificare una licenza diversa è l'inclusione di un collegamento alla licenza tramite LicenseURI in PSData.
Un esempio è disponibile nell'argomento Recommended Manifest Fields (Campi manifesto consigliati).

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Firmare il codice

La firma del codice offre agli utenti il massimo livello di garanzia per quanto riguarda l'autore del pacchetto e l'autenticità del codice acquisito.
Per altre informazioni generali sulla firma del codice, vedere [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=106296) (Introduzione alla firma del codice).
PowerShell supporta la convalida della firma del codice con due approcci principali:

- Firma dei file di script
- Firma di moduli mediante catalogo

La firma dei file di PowerShell è un metodo consolidato e garantisce che il codice eseguito è stato generato da una fonte attendibile e non è stato modificato.
Informazioni dettagliate sulla firma dei file di script di PowerShell sono disponibili nell'argomento [About signing](/powershell/module/microsoft.powershell.core/about/about_signing) (Informazioni sulla firma).
Per riassumere, è possibile aggiungere una firma a qualsiasi file PS1 convalidato da PowerShell quando viene caricato lo script.
È possibile vincolare PowerShell all'uso di script firmati con i cmdlet dei [criteri di esecuzione](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

La firma di moduli mediante catalogo è una funzionalità aggiunta in PowerShell 5.1.
Le modalità per la firma di un modulo sono descritte nell'argomento [Cmdlet di catalogo](/powershell/wmf/5.1/catalog-cmdlets).
Per riassumere, la firma mediante catalogo viene eseguita creando un file di catalogo che contiene un valore hash per ogni file nel modulo, quindi firmando questo file.
I cmdlet PowerShellGet publish-module, install-module, save-module e update-module verificano la validità della firma, quindi confermano che il valore hash di ogni pacchetto corrisponda a quello presente nel catalogo.
Se nel sistema è installata una versione precedente del modulo, install-module verifica che l'autorità di firma della nuova versione corrisponda a quella dell'installazione precedente.
La firma mediante catalogo può essere usata insieme alla firma dei file di script ma non la sostituisce. PowerShell non convalida le firme del catalogo al caricamento del modulo.

## <a name="follow-semver-guidelines-for-versioning"></a>Osservare le linee guida SemVer per il controllo delle versioni

[SemVer](http://semver.org/) è una convenzione pubblica che descrive come strutturare e cambiare una versione per facilitare l'interpretazione delle modifiche.
La versione del pacchetto deve essere inclusa nei dati del manifesto.

- La versione deve essere strutturata con 3 blocchi numerici separati da punti, ad esempio 0.1.1 o 4.11.192
- Le versioni che iniziano con "0" indicano che il pacchetto non è ancora pronto per la produzione e il primo numero dovrebbe iniziare con "0" solo se è l'unico numero usato
- La modifica del primo numero (da 1.9.9999 a 2.0.0) indica modifiche strutturali di primaria importanza alla versione.
- La modifica del secondo numero (da 1.01 a 1.02) indica modifiche a livello di funzionalità, ad esempio l'aggiunta di nuovi cmdlet a un modulo.
- La modifica del terzo numero indica modifiche meno importanti, ad esempio l'aggiunta di nuovi parametri, esempi aggiornati o nuovi test.
- Per la creazione di elenchi di versioni in PowerShell le versioni vengono ordinate come stringhe, quindi 1.01.0 verrà considerato maggiore di 1.001.0.

L'applicazione PowerShell è stata creata prima della pubblicazione di SemVer, pertanto supporta la maggior parte degli elementi di SemVer ma non tutti, in particolare:

- Non supporta le stringhe di versione provvisoria nei numeri di versione. Ciò è utile quando un autore vuole rilasciare una versione di anteprima di una nuova versione principale dopo aver rilasciato la versione 1.0.0. Questa funzionalità verrà supportata in una versione futura dei cmdlet di PowerShell Gallery e PowerShellGet.
- PowerShell e PowerShell Gallery supportano le stringhe di versione con 1, 2 e 4 segmenti. Molti moduli meno recenti non seguivano queste linee guida e le versioni dei prodotti Microsoft includono le informazioni sulla build in un quarto blocco di numeri, ad esempio 5.1.14393.1066. Dal punto di vista del controllo delle versioni, queste differenze vengono ignorate.

## <a name="test-using-a-local-repository"></a>Eseguire test usando un repository locale

PowerShell Gallery non è progettato per essere usato come destinazione per il testing del processo di pubblicazione.
Il modo migliore per testare l'intero processo di pubblicazione in PowerShell Gallery prevede la configurazione e l'uso di un repository personale locale.
Questa operazione può essere eseguita in svariati modi, ad esempio:

- Configurare un'istanza locale di PowerShell Gallery, usando il [progetto di PS Gallery privato](https://github.com/PowerShell/PSPrivateGallery) in Github. Questo progetto di anteprima consente di configurare un'istanza di PowerShell Gallery che è possibile controllare e usare per i test.
- Configurare un [repository NuGet interno](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Questa alternativa richiede un maggiore impegno per la configurazione, ma offre il vantaggio di poter convalidare un maggior numero di requisiti, in particolare l'uso di una chiave API e la presenza o meno delle dipendenze nella destinazione durante la pubblicazione.
- Configurare una condivisione file come "repository" di test. Si tratta di una soluzione semplice da configurare, ma trattandosi di una condivisione file, le convalide indicate in precedenza non verranno eseguite. Uno dei vantaggi potenziali in questo caso è che la condivisione file non controlla la chiave API (obbligatoria), pertanto è possibile usare la stessa chiave usata per pubblicare in PowerShell Gallery.

Con una qualsiasi di queste soluzioni, usare Register-PSRepository per definire un nuovo "repository", che verrà usato nella proprietà -Repository per Publish-Module.

Per la pubblicazione di test è importante evidenziare un altro aspetto. Qualsiasi pacchetto pubblicato in PowerShell Gallery non può essere eliminato senza l'assistenza del team operativo che dovrà confermare che non esistano dipendenze per il pacchetto che si desidera pubblicare.
Questo è il motivo per cui PowerShell Gallery non è supportato come destinazione di testing e per cui verrà contattato qualsiasi autore che prova a usarlo a questo scopo.

## <a name="use-powershellget-to-publish"></a>Usare PowerShellGet per la pubblicazione

È consigliabile che gli autori della pubblicazione usino i cmdlet Publish-Module e Publish-Script quando lavorano con PowerShell Gallery.
PowerShellGet è stato creato per evitare che vengano memorizzate informazioni importanti sull'installazione da e la pubblicazione in PowerShell Gallery.
In alcuni casi, gli autori della pubblicazione hanno scelto di ignorare PowerShellGet e usare il client NuGet, o i cmdlet PackageManagement, invece di Publish-Module.
Molti dettagli vengono facilmente omessi, il che genera richieste di supporto di vario genere.

In presenza di un motivo che rende impossibile l'uso di Publish-Module o Publish-Script, segnalarlo.
Segnalare un problema nel repository GitHub di PowerShellGet e specificare i dettagli che determinano la scelta di NuGet o PackageManagement.

## <a name="recommended-workflow"></a>Flusso di lavoro consigliato

L'approccio più efficace per i pacchetti pubblicati in PowerShell Gallery è il seguente:

- Eseguire lo sviluppo iniziale in un sito di progetto open-source. Il team di PowerShell usa GitHub.
- Usare i commenti e suggerimenti dei revisori e [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer) per portare il codice a una condizione stabile.
- Includere la documentazione per comunicare agli altri utenti come usare il codice.
- Testare l'azione di pubblicazione usando un repository locale.
- Pubblicare una versione stabile o alfa in PowerShell Gallery e includere la documentazione e il collegamento al sito del progetto.
- Raccogliere il feedback e sviluppare il codice nel sito di progetto, quindi pubblicare gli aggiornamenti stabili in PowerShell Gallery.
- Aggiungere esempi e test Pester nel progetto e nel modulo.
- Decidere se firmare il codice del pacchetto
- Quando si ritiene che il progetto sia pronto per l'uso in un ambiente di produzione, pubblicare la versione 1.0.0 in PowerShell Gallery.
- Continuare a raccogliere commenti e suggerimenti e sviluppare ulteriormente il codice in base all'input degli utenti.

