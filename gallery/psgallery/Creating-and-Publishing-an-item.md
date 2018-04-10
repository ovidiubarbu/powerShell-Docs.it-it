---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Creazione e pubblicazione di un elemento
ms.openlocfilehash: bbe9095b438e2ddb72a04055d1f05fbf20d4404a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="creating-and-publishing-an-item"></a>Creazione e pubblicazione di un elemento
In PowerShell Gallery è possibile pubblicare e condividere moduli e script PowerShell stabili e risorse DSC con la più ampia community di utenti di PowerShell.

In questo articolo vengono illustrati i meccanismi e i passaggi importanti per preparare uno script o un modulo e pubblicarlo in PowerShell Gallery.
È consigliabile rivedere le [linee guida per la pubblicazione](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) per capire in che modo verificare che gli elementi pubblicati siano ampiamente accettati dagli utenti di PowerShell Gallery.

I requisiti minimi per la pubblicazione di un elemento in PowerShell Gallery sono i seguenti:

* Avere un account PowerShell Gallery e la chiave API ad esso associata
* Verificare che i metadati necessari siano inclusi nell'elemento
* Usare gli strumenti di pre-convalida per verificare che l'elemento sia pronto per essere pubblicato
* Pubblicare l'elemento in PowerShell Gallery usando i comandi Publish-Module e Publish-Script
* Capacità di rispondere alle domande o ai dubbi che riguardano l'elemento

PowerShell Gallery accetta moduli e script PowerShell.
Con script si intende uno script PowerShell che sia un singolo file e non faccia parte di un modulo più grande.

## <a name="powershell-gallery-account-and-api-key"></a>Account e chiave API di PowerShell Gallery
Vedere [Creating a PowerShell Gallery Account](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) (Creazione di un account PowerShell Gallery) per informazioni su come configurare un account PowerShell Gallery.

Dopo aver creato un account, è possibile ottenere la chiave API necessaria per pubblicare un elemento.
Dopo aver eseguito l'accesso con l'account, il nome utente sarà visualizzato nella parte superiore delle pagine di PowerShell Gallery al posto di Register (Registrazione).
Facendo clic sul proprio nome utente si aprirà la pagina My Account (Account personale), nella quale è contenuta la chiave API.

Nota: usare la chiave API in modo sicuro come per account di accesso e password.
Con questa chiave chiunque può infatti aggiornare qualsiasi elemento in PowerShell Gallery.
È consigliabile aggiornare la chiave regolarmente, usando il comando Reset Key (Ripristina chiave) nella pagina My Account (Account personale).

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Metadati necessari per gli elementi pubblicati in PowerShell Gallery

PowerShell Gallery offre informazioni agli utenti della raccolta ottenendole dai campi dei metadati inclusi nel manifesto dello script o del modulo.
Per creare o modificare gli elementi che saranno pubblicati in PowerShell Gallery esistono alcuni semplici requisiti relativi alle informazioni definite nel manifesto dell'elemento.
È consigliabile rivedere la sezione relativa ai metadati dell'elemento nelle [linee guida per la pubblicazione](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) per sapere come offrire agli utenti le informazioni più appropriate insieme agli elementi.

I cmdlet [New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) e [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) creano il modello di manifesto con segnaposto per tutti gli elementi del manifesto.

Entrambi i manifesti contengono due sezioni importanti per la pubblicazione, vale a dire Key Primary Data (Dati chiave primaria) e l'area PSData di PrivateData. I dati della chiave primaria in un manifesto del modulo PowerShell corrispondono a tutti gli elementi esterni alla sezione PrivateData.
Le chiavi primarie sono correlate alla versione di PowerShell in uso. Non sono supportate chiavi non definite.
PrivateData supporta l'aggiunta di nuove chiavi, in modo che gli elementi specifici per PowerShell Gallery siano contenuti in PSData.


Gli elementi del manifesto più importanti da compilare per la pubblicazione dell'elemento in PowerShell Gallery sono i seguenti:

* Nome dello script o del modulo: questi nomi ottenuti dai nomi di .PS1 per uno script o di .PSD1 per un modulo.
* Versione: si tratta di una chiave primaria obbligatoria. Il formato deve rispettare le linee guida SemVer (per i dettagli, vedere le procedure consigliate)
* Autore: si tratta di una chiave primaria obbligatoria. Contiene il nome da associare all'elemento (vedere le informazioni su autori e proprietari riportate di seguito)
* Descrizione: si tratta di una chiave primaria obbligatoria. Viene usata per illustrare brevemente lo scopo di questo elemento e gli eventuali requisiti per il suo uso
* ProjectURI: si tratta di un campo URI consigliato in PSData che contiene un collegamento a un repository Github o percorso simile in cui è possibile sviluppare l'elemento

Gli autori e i proprietari degli elementi di PowerShell Gallery sono concetti correlati, ma non sempre corrispondenti.
I proprietari di un elemento sono gli utenti che hanno un account PowerShell Gallery e autorizzazione per gestire l'elemento. È possibile che gli elementi siano aggiornabili da molti proprietari.
Il proprietario è disponibile solo da PowerShell Gallery e viene perso se l'elemento viene copiato da un sistema in un altro.
L'autore è una stringa compilata nei dati del manifesto. Fa pertanto sempre parte dell'elemento.
Di seguito sono riportati i consigli per gli elementi di prodotti Microsoft:

* Avere più proprietari. Almeno uno deve essere il nome del team che produce l'elemento;
* L'autore deve essere il nome di un team noto (ad esempio il team di Azure SDK) o Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Pre-convalidare l'elemento

Prima di pubblicare l'elemento in PowerShell Gallery, è necessario eseguire alcuni strumenti per analizzare il codice:

* [PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) disponibile in PowerShell Gallery
* Per i moduli, Test-ModuleManifest che fa parte di PowerShell
* Per gli script, Test-ScriptFileInfo disponibile in PowerShellGet

[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) è uno strumento di analisi del codice statico che analizza il codice per verificare che soddisfi le linee guida di base sulla codifica di PowerShell. Questo strumento identifica problemi critici e comuni nel codice. È consigliabile eseguirlo regolarmente durante lo sviluppo per verificare che l'elemento sia pronto per la pubblicazione.
PowerShell Script Analyzer elenca i problemi identificandoli come errori, avviso e informazioni.
Tutti gli errori devono essere risolti prima che l'elemento venga pubblicato in PowerShell Gallery. Gli avvisi devono essere esaminati e per lo più risolti.
Eseguire PowerShell Script Analyzer ogni volta che un elemento viene pubblicato o aggiornato in PowerShell Gallery.
Il team operativo di PowerShell Gallery contatterà i proprietari affinché risolvano gli errori riscontrati.

Se le informazioni sul manifesto contenute nell'elemento non possono essere lette dall'infrastruttura di PowerShell Gallery, l'elemento non potrà essere pubblicato.
[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) intercetta i problemi comuni che possono rendere inutilizzabile il modulo dopo essere stato installato. Eseguire questo strumento per ogni modulo prima che sia pubblicato in PowerShell Gallery.

Analogamente [Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) convalida i metadati in uno script. Eseguire questo strumento su ogni script (pubblicato separatamente da un modulo) prima che sia pubblicato in Powershell Gallery.


## <a name="publishing-items"></a>Pubblicazione degli elementi

Per pubblicare gli elementi in PowerShell Gallery, è necessario usare i cmdlet [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) o [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module).
Entrambi i comandi richiedono

* Il percorso dell'elemento da pubblicare. Per un modulo, usare la cartella denomina per il modulo. Se si specifica una cartella che contiene più versioni dello stesso modulo, è necessario specificare il parametro RequiredVersion.
* Una chiave API NuGet. Si tratta della chiave API disponibile nella pagina My Account (Account personale) in PowerShell Gallery.

La maggior parte delle altre opzioni nella riga di comando deve essere contenuta nei dati del manifesto per l'elemento che sarà pubblicato. Non è pertanto necessario specificarle nel comando.

Per evitare errori, è consigliabile provare i comandi usando Whatif-Verbose, prima della pubblicazione.
Questa operazione consente di velocizzare il processo, in quanto ogni volta che si pubblica in PowerShell Gallery, è necessario aggiornare il numero di versione nella sezione manifesto dell'elemento.

Alcuni esempi: 'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'

Esaminare attentamente l'output e se non vengono visualizzati errori o avvisi, ripetere il comando senza - Whatif.

Tutti gli elementi pubblicati in PowerShell Gallery vengono analizzati da PowerShell Script Analyzer e vengono sottoposti ad analisi per rilevare eventuali virus.
I problemi qui riscontrati vengono inviati all'autore della pubblicazione perché li risolva.

Dopo aver pubblicato un elemento in PowerShell Gallery, è necessario controllare i commenti e suggerimenti sull'elemento.

* Monitorare l'indirizzo di posta elettronica associato all'account usato per la pubblicazione.
Gli utenti e il team operativo di PowerShell Gallery invieranno commenti e suggerimenti tramite tale account, inclusi i problemi riscontrati da PowerShell Script Analyzer o dall'analisi dei virus.
Se l'account di posta elettronica non è valido o se all'account vengono segnalati gravi problemi che restano a lungo irrisolti, gli elementi possono essere considerati abbandonati e saranno pertanto rimossi da PowerShell Gallery come descritto in [Condizioni per l'utilizzo](https://www.powershellgallery.com/policies/Terms).
* È consigliabile sottoscrivere i commenti per ogni elemento pubblicato in PowerShell Gallery.
In questo modo è possibile ricevere una notifica se uno degli elementi in PowerShell Gallery viene commentato.
È facoltativo, poiché richiede la creazione di un account con LiveFyre.