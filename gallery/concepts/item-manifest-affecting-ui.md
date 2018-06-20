---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Valori del manifesto degli elementi con effetti sull'interfaccia utente di PowerShell Gallery
ms.openlocfilehash: 39522396b179c54b981e6292cddacec27b32506c
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048494"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Valori del manifesto degli elementi con effetti sull'interfaccia utente di PowerShell Gallery

Questo argomento offre informazioni di riepilogo per gli editori sulle procedure per modificare il manifesto per le pubblicazioni di PowerShell Gallery, con effetti sulle funzionalità dei cmdlet PowerShellGet e sull'interfaccia utente di PowerShell Gallery.
Il contenuto è organizzato in base alla posizione in cui comparirà la modifica, a partire dalla sezione centrale per poi procedere con l'area di spostamento a sinistra. È disponibile una sezione di informazioni dettagliate sui tag, nella quale sono identificati i tag importanti, oltre ad alcuni dei tag usati più comunemente.
La documentazione include anche due argomenti con esempi di manifesto:

- Per i moduli, vedere [Aggiornare il manifesto del modulo](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest)
- Per gli script, vedere [Creare i file di script con i metadati](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Elementi di funzionalità di PowerShell Gallery controllati dal manifesto

La tabella seguente illustra gli elementi dell'interfaccia utente della pagina degli elementi di PowerShell Gallery controllati dall'editore.
Per ogni elemento viene indicato se può essere controllato dal manifesto del modulo o dello script.

| Elemento dell'interfaccia utente | Description | Modulo | Script |
| --- | --- | --- | --- |
| **Titolo** | Si tratta del nome dell'elemento pubblicato in PowerShell Gallery  | No | No |
| **Versione** | La versione visualizzata è la stringa di versione nei metadati, con versione non definitiva se specificata. La parte principale della versione in un manifesto del modulo è rappresentata da ModuleVersion. Nel caso di uno script è identificata come .VERSION. Se viene specificata una stringa di versione non definitiva, verrà aggiunta a ModuleVersion per i moduli o specificata come parte di .VERSION per gli script. È disponibile documentazione su come specificare le stringhe di versione non definitiva nei [moduli](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule) negli [script](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript). | Sì | Sì |
| **Descrizione** | Queste informazioni corrispondono a Description nel manifesto del modulo e a .DESCRIPTION nel manifesto del file di script. | Sì | Sì |
| **Richiedi accettazione della licenza** | Un modulo può richiedere che l'utente accetti una licenza, modificando il manifesto del modulo con RequireLicenseAcceptance = $true, specificando un LicenseURI e fornendo un file license.txt nella radice della cartella del modulo. Ulteriori informazioni sono disponibili nell'argomento [Richiedi accettazione della licenza](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance). | Sì | No |
| **Note sulla versione** | Per i moduli, queste informazioni vengono recuperate dalla sezione ReleaseNotes in PSData\PrivateData. Nei manifesti degli script corrisponde all'elemento .RELEASENOTES. | Sì | Sì |
| **Proprietari** | I proprietari sono l'elenco di utenti autorizzati ad aggiornare un elemento in PowerShell Gallery. L'elenco dei proprietari non è incluso nel manifesto degli elementi. È disponibile documentazione aggiuntiva che descrive come [gestire i proprietari degli elementi](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | No | No |
| **Autore** | Queste informazioni vengono incluse nel manifesto del modulo come Author e nel manifesto di uno script come .AUTHOR. Il campo Author viene spesso usato per specificare una società o un'organizzazione associata a un elemento. | Sì | Sì |
| **Copyright** | Queste informazioni corrispondono al campo Copyright nel manifesto del modulo e a .COPYRIGHT nel manifesto di uno script. | Sì | Sì |
| **FileList** | L'elenco dei file viene ricavato dal pacchetto quando viene pubblicato in PowerShell Gallery. Non è controllabile tramite le informazioni del manifesto. Nota: per ogni elemento in PowerShell Gallery viene elencato un file aggiuntivo con estensione nuspec, che non è presente dopo aver installato l'elemento in un sistema. Si tratta del manifesto del pacchetto NuGet per l'elemento e può essere ignorato. | No | No |
| **Tag** | Per i moduli, i tag sono inclusi in PSData\PrivateData. Per gli script, viene usata la sezione .TAGS. Si noti che i tag non possono contenere spazi, anche tra virgolette. Per i tag esistono altri requisiti e significati, descritti più avanti in questo argomento nella sezione Dettagli dei tag. | Sì | Sì |
| **Cmdlet** | Queste informazioni vengono specificate nel manifesto del modulo tramite CmdletsToExport. Si noti che la procedura consigliata prevede di elencare gli elementi in modo esplicito, invece di usare il carattere jolly "*", perché consentirà di migliorare le prestazioni di caricamento del modulo per gli utenti. | Sì | No |
| **Functions** | Queste informazioni vengono specificate nel manifesto del modulo tramite FunctionsToExport. Si noti che la procedura consigliata prevede di elencare gli elementi in modo esplicito, invece di usare il carattere jolly "*", perché consentirà di migliorare le prestazioni di caricamento del modulo per gli utenti. | Sì | No |
| **Risorse DSC** | Per i moduli che verranno usati in PowerShell versione 5.0 e versioni successive, queste informazioni vengono specificate nel manifesto tramite DscResourcesToExport. Se il modulo deve essere usato in PowerShell 4, è sconsigliabile usare DSCResourcesToExport perché non è una chiave di manifesto supportata. (DSC non era disponibile prima di PowerShell 4.) | Sì | No |
| **Flussi di lavoro** | I flussi di lavoro vengono pubblicati in PowerShell Gallery come script e identificati come flussi di lavoro nel codice (vedere [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) per un esempio). Queste informazioni non sono controllate dal manifesto. | No | No |
| **Funzionalità di ruolo** | Queste informazioni verranno presentate quando il modulo pubblicato in PowerShell Gallery contiene uno o più file di funzionalità di ruolo (con estensione psrc), usati da JEA. Vedere la documentazione di JEA per altri dettagli sulle [funzionalità di ruolo](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Sì | No |
| **Edizioni di PowerShell** | Queste informazioni vengono specificate nel manifesto di uno script o del modulo. Per i moduli progettati per essere usati con PowerShell 5.0 e versioni precedenti, queste informazioni sono controllate tramite tag. Per l'edizione Desktop usare il tag PSEdition_Desktop e per l'edizione Core usare il tag PSEdition_Core. Per i moduli che verranno usati solo in PowerShell 5.1 e versioni successive, è disponibile la chiave CompatiblePSEditions nel manifesto principale. Per altri dettagli, vedere le funzionalità per le edizioni di PowerShell nella [documentazione di PowerShellGet](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Sì | Sì |
| **Dipendenze** | Le dipendenze sono i moduli in PowerShell Gallery dichiarati nel modulo come RequiredModules o nel manifesto di script come #Requires –Module (nome). | Sì | Sì |
| **Versione minima di PowerShell** | Queste informazioni possono essere specificate in un manifesto del modulo come PowerShellVersion | Sì | No |
| **Cronologia versioni** | La cronologia delle versioni riflette gli aggiornamenti apportati a un modulo in PowerShell Gallery. Se una versione di un elemento viene nascosta tramite la funzionalità di eliminazione, non verrà visualizzata nella cronologia delle versioni, se non per i proprietari dell'elemento. | No | No |
| **Sito di progetto** | Il sito di progetto viene specificato per i moduli nella sezione Privatedata\PSData del manifesto del modulo tramite un ProjectURI. Nel manifesto di uno script queste informazioni sono controllate tramite .PROJECTURI. | Sì | Sì |
| **Licenza** | È possibile specificare un collegamento alla licenza per i moduli nella sezione Privatedata\PSData del manifesto del modulo tramite un LicenseURI. Nel manifesto di uno script queste informazioni sono controllate tramite .LICENSEURI. È importante notare che se non viene specificata una licenza tramite LicenseURI, o in un modulo, le condizioni per l'utilizzo dell'elemento sono quelle definite per PowerShell Gallery. Vedere le condizioni per l'utilizzo per altri dettagli. | Sì | Sì |

## <a name="editing-item-details"></a>Modifica dei dettagli degli elementi

La pagina Modifica elemento di PowerShell Gallery consente agli editori di modificare vari campi visualizzati per un elemento, in particolare:

- Title
- Description
- Riepilogo
- URL dell'icona
- URL della pagina iniziale del progetto
- Autori
- Copyright
- Tag
- Note sulla versione
- Richiesta della licenza

Questo approccio non è in genere consigliato, eccetto quando è necessario per correggere le informazioni visualizzate per una versione precedente di un modulo.
Gli utenti che acquisiscono il modulo vedranno che i metadati non corrispondono a ciò che viene visualizzato in PowerShell Gallery, con conseguenti dubbi in merito all'elemento.
Ciò causerà di frequente l'invio di richieste ai proprietari dell'elemento per avere conferme in merito alle modifiche.
Ogni volta che si usa questo approccio è consigliabile pubblicare una nuova versione dell'elemento con le stesse modifiche.

## <a name="tag-details"></a>Dettagli dei tag

I tag sono semplici consumer di stringhe usati per trovare gli elementi.
I tag risultano particolarmente utili quando vengono usati in modo coerente per molti elementi correlati allo stesso argomento. L'uso di più varianti della stessa parola (ad esempio elemento ed elementi o test e testing) offre in genere pochi vantaggi.
I tag sono stringhe composte da una sola parola senza distinzione tra maiuscole e minuscole e non possono includere spazi vuoti. In presenza di una frase che si ritiene possa essere utile per la ricerca da parte degli utenti, aggiungerla alla descrizione dell'elemento in modo che compaia nei risultati della ricerca. Usare la convenzione Pascal per maiuscole/minuscole, trattini, caratteri di sottolineatura o punti se occorre per migliorare la leggibilità. Prestare attenzione quando si creano tag lunghi, complessi e non comuni, perché spesso contengono errori di ortografia.

È importante evidenziare alcuni tag, perché vengono gestiti in modo speciale da PowerShell Gallery e dai cmdlet PowerShellGet. PSEdition_Desktop e PSEdition_Core sono esempi specifici e sono descritti più indietro.

Come già indicato, i tag sono utili soprattutto quando sono specifici e vengono usati in modo coerente per molti elementi.
Per un editore che cerca di individuare i tag migliori da usare, il modo più semplice consiste nel cercare i tag che si stanno valutando in PowerShell Gallery.
Il risultato ideale è che vengano restituiti molti elementi e che le descrizioni degli elementi siano in linea con l'uso previsto delle parole chiave.

Per riferimento, ecco alcuni dei tag usati più di frequente alla data del 14/12/2017.
In alcuni casi, a fianco del tag sono indicate opzioni simili, ma meno ottimali.
È consigliabile usare il tag preferito, perché produce meno risultati non significativi e migliori risultati di ricerca per gli utenti.


| **Tag preferito** | **Alternative e note** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration è meno consigliato perché troppo lungo |
| **ResourceManager** | L'acronimo ARM viene usato per descrivere un gruppo di processori, quindi è sconsigliabile usarlo per Azure Resource Manager | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automation** |  |
| **REST** |  |
| **ActiveDirectory** | AD non è attualmente usato da solo  |
| **SQLServer** |  |
| **DBA** |  |
| **Sicurezza** | Defense è meno preciso |
| **Database** | Il plurale inglese databases è meno consigliato |
| **DevOps** |  |
| **Windows** |  |
| **Build** |  |
| **Deployment** | Il verbo deploy è usato meno frequentemente |
| **Cloud** |  |
| **GIT** |  |
| **Test** | Testing è meno consigliato |
| **VersionControl** | Version è meno preciso, anche se usato più frequentemente  |
| **Logging** | Uso preferito come azione |
| **Log** | Uso preferito come oggetto |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Storage** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Network** | Il tag networking è simile, ma meno usato |
| **SharePoint** |  |
| **Reporting** | Reporting è un'azione, report è un oggetto |
| **Report** | Report è un oggetto |
| **WinRM** |  |
| **Monitoring** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Color** |  |
| **DNS** |  |
| **Office365** | È preferibile indicare Office per intero. Il tag O365 è usato meno comunemente, sebbene più breve | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | HyperV è usato meno comunemente come tag |
| **Configuration** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Firewall** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Usato principalmente per i moduli AzureRM |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |