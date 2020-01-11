---
title: Progettazione del provider di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: bfb29fd5df87ffa9ae270c18ce8bfb0c59ee6f90
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870660"
---
# <a name="designing-your-windows-powershell-provider"></a>Progettazione del provider di Windows PowerShell

È necessario implementare un provider di Windows PowerShell se il prodotto o la configurazione espone un set di dati archiviati, ad esempio un database che l'utente desidera esplorare o esplorare. Inoltre, se il prodotto fornisce un contenitore, anche se non si tratta di un contenitore multilivello, è opportuno implementare un provider di Windows PowerShell. Ad esempio, potrebbe essere necessario implementare un provider di contenitori di Windows PowerShell se il verbo del cmdlet Copy, Move, Rename, New o Remove ha senso come un'operazione sui dati di configurazione o del prodotto.

## <a name="windows-powershell-paths-identify-your-provider"></a>Percorsi di Windows PowerShell per identificare il provider

Il runtime di Windows PowerShell usa i percorsi di Windows PowerShell per accedere al provider di Windows PowerShell appropriato. Quando un cmdlet specifica uno di questi percorsi, il runtime sa quale provider utilizzare per accedere all'archivio dati associato. Questi percorsi includono percorsi qualificati per l'unità, percorsi qualificati dal provider, percorsi diretti del provider e percorsi interni del provider. Ogni provider di Windows PowerShell deve supportare uno o più di questi percorsi.

Per ulteriori informazioni sui percorsi di Windows PowerShell, vedere funzionamento di Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definizione di un percorso qualificato dall'unità

Per consentire all'utente di accedere ai dati che si trovano in un'unità fisica, il provider di Windows PowerShell deve supportare un percorso qualificato dall'unità. Questo percorso inizia con il nome dell'unità seguito da due punti (:), ad esempio, unità: \ abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definizione di un percorso qualificato dal provider

Per consentire al runtime di Windows PowerShell di inizializzare e annullare l'inizializzazione del provider, il provider di Windows PowerShell deve supportare un percorso qualificato dal provider. Ad esempio, FileSystem::\\\uncshare\abc\bar è il percorso qualificato dal provider per il provider FileSystem fornito da Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definizione di un percorso diretto del provider

Per consentire l'accesso remoto al provider di Windows PowerShell, deve supportare un percorso diretto del provider da passare direttamente al provider di Windows PowerShell per il percorso corrente. Ad esempio, il provider del registro di sistema di Windows PowerShell può usare \\\server\regkeypath come percorso diretto del provider.

### <a name="defining-a-provider-internal-path"></a>Definizione di un percorso interno del provider

Per consentire al cmdlet del provider di accedere ai dati usando le API (Application Programming Interface) non Windows PowerShell, il provider di Windows PowerShell deve supportare un percorso interno del provider. Questo percorso è indicato dopo "::" nel percorso qualificato dal provider. Ad esempio, il percorso interno del provider per il provider FileSystem di Windows PowerShell è \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Modifica dei dati archiviati

Quando si esegue l'override dei metodi che modificano l'archivio dati sottostante, chiamare sempre il metodo [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) con la versione più aggiornata dell'elemento modificato da tale metodo. L'infrastruttura del provider determina se l'oggetto item deve essere passato alla pipeline, ad esempio quando l'utente specifica il parametro-PassThru. Se il recupero dell'elemento più aggiornato è un'operazione costosa (prestazioni), è possibile testare la proprietà Context. PassThru per determinare se è effettivamente necessario scrivere l'elemento risultante.

## <a name="choose-a-base-class-for-your-provider"></a>Scegliere una classe di base per il provider

Windows PowerShell offre una serie di classi di base che è possibile usare per implementare il proprio provider di Windows PowerShell. Quando si progetta un provider, scegliere la classe di base, descritta in questa sezione, più adatta ai propri requisiti.

Ogni classe base del provider di Windows PowerShell rende disponibile un set di cmdlet. In questa sezione vengono descritti i cmdlet di, ma non vengono descritti i relativi parametri.

Utilizzando lo stato della sessione, il runtime di Windows PowerShell rende disponibili diversi cmdlet Location per determinati provider di Windows PowerShell, ad esempio i cmdlet `Get-Location`, `Set-Location`, `Pop-Location`e `Push-Location`. È possibile utilizzare il cmdlet `Get-Help` per ottenere informazioni su questi cmdlet Location.

### <a name="cmdletprovider-base-class"></a>Classe di base CmdletProvider

La classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) definisce un provider di base di Windows PowerShell. Questa classe supporta la dichiarazione del provider e fornisce una serie di proprietà e metodi disponibili per tutti i provider di Windows PowerShell.
La classe viene richiamata dal cmdlet `Get-PSProvider` per elencare tutti i provider disponibili per una sessione.
L'implementazione di questo cmdlet viene fornita dallo stato della sessione.

> [!NOTE]
> I provider di Windows PowerShell sono disponibili per tutti gli ambiti del linguaggio di Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Classe di base DriveCmdletProvider

La classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) definisce un provider di unità di Windows PowerShell che supporta operazioni per l'aggiunta di nuove unità, la rimozione di unità esistenti e l'inizializzazione di unità predefinite. Ad esempio, il provider FileSystem fornito da Windows PowerShell Inizializza le unità per tutti i volumi montati, ad esempio le unità disco rigido e i dispositivi CD/DVD.

Questa classe deriva dalla classe di base [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Nella tabella seguente sono elencati i cmdlet esposti da questa classe. Oltre a quelle elencate, il cmdlet `Get-PSDrive` (esposto da stato sessione) è un cmdlet correlato usato per recuperare le unità disponibili.

|      Cmdlet      |                             Definizione                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | Crea una nuova unità per la sessione e trasmette le informazioni sull'unità. |
| `Remove-PSDrive` | Rimuove un'unità dalla sessione.                                   |

### <a name="itemcmdletprovider-base-class"></a>Classe di base ItemCmdletProvider

La classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) definisce un provider di elementi di Windows PowerShell che esegue operazioni sui singoli elementi dell'archivio dati e non presuppone alcuna funzionalità di spostamento o contenitore. Questa classe deriva dalla classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Nella tabella seguente sono elencati i cmdlet esposti da questa classe.

|     Cmdlet     |                                                                                                                                                            Definizione                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | Cancella il contenuto corrente degli elementi nella posizione specificata e lo sostituisce con il valore "Clear" specificato dal provider. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.                                                                                   |
| `Get-Item`     | Recupera gli elementi dal percorso specificato ed esegue il flusso degli oggetti risultanti.                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | Richiama l'azione predefinita per l'elemento nel percorso specificato.                                                                                                                                                                                                                                                                   |
| `Set-Item`     | Imposta un elemento in corrispondenza della posizione specificata con il valore indicato. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.                                                                                                                                                   |
| `Resolve-Path` | Risolve i caratteri jolly per un percorso di Windows PowerShell e le informazioni sul percorso dei flussi.                                                                                                                                                                                                                                              |
| `Test-Path`    | Verifica il percorso specificato e restituisce `true` se esiste e `false` in caso contrario. Questo cmdlet viene implementato per supportare il `IsContainer` parametro per il metodo [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) . |

### <a name="containercmdletprovider-base-class"></a>Classe di base ContainerCmdletProvider

La classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) definisce un provider di contenitori di Windows PowerShell che espone all'utente un contenitore, per gli elementi dell'archivio dati. Tenere presente che un provider di contenitori di Windows PowerShell può essere utilizzato solo quando è presente un contenitore (nessun contenitore annidato) con elementi. Se sono presenti contenitori annidati, è necessario implementare un provider di navigazione di Windows PowerShell.

Questa classe deriva dalla classe di base [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Nella tabella seguente vengono definiti i cmdlet implementati da questa classe.

|     Cmdlet      |                                                                        Definizione                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | Copia gli elementi da una posizione a un'altra. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`. |
| `Get-Childitem` | Recupera gli elementi figlio nel percorso specificato e li trasmette come oggetti.                                                                        |
| `New-Item`      | Crea nuovi elementi in corrispondenza della posizione specificata e trasmette l'oggetto risultante.                                                                           |
| `Remove-Item`   | Rimuove gli elementi dalla posizione specificata.                                                                                                               |
| `Rename-Item`   | Rinomina un elemento nella posizione specificata. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`. |

### <a name="navigationcmdletprovider-base-class"></a>Classe di base NavigationCmdletProvider

La classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) definisce un provider di navigazione di Windows PowerShell che esegue operazioni per gli elementi che usano più di un contenitore. Questa classe deriva dalla classe di base [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Nella tabella seguente sono elencati i cmdlet esposti da questa classe.

|    Cmdlet    |                                                                      Definizione                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Combina-percorso | Combina due percorsi in un singolo percorso, usando un delimitatore specifico del provider tra i percorsi. Questo cmdlet trasmette le stringhe.                               |
| `Move-Item`  | Sposta gli elementi nel percorso specificato. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`. |

Un cmdlet correlato è il cmdlet parse-path di base fornito da Windows PowerShell. Questo cmdlet può essere usato per analizzare un percorso di Windows PowerShell per supportare il parametro `Parent`. Trasmette la stringa del percorso padre.

## <a name="select-provider-interfaces-to-support"></a>Selezionare le interfacce del provider da supportare

Oltre a derivare da una delle classi di base di Windows PowerShell, il provider di Windows PowerShell può supportare altre funzionalità derivando da una o più delle seguenti interfacce del provider. Questa sezione definisce le interfacce e i cmdlet supportati da ciascuno di essi. Non vengono descritti i parametri per i cmdlet supportati dall'interfaccia. Le informazioni sui parametri dei cmdlet sono disponibili online usando i cmdlet `Get-Command` e `Get-Help`.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

L'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) definisce un provider di contenuti che esegue operazioni sul contenuto di un elemento di dati. Nella tabella seguente sono elencati i cmdlet esposti da questa interfaccia.

|     Cmdlet      |                                                                                        Definizione                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | Aggiunge le lunghezze di valore indicate al contenuto dell'elemento specificato. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`. |
| `Clear-Content` | Imposta il contenuto dell'elemento specificato sul valore "Clear". Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.               |
| `Get-Content`   | Recupera il contenuto degli elementi specificati e trasmette i flussi degli oggetti risultanti.                                                                                                         |
| `Set-Content`   | Sostituisce il contenuto esistente per gli elementi specificati. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.                     |

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

L'interfaccia [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) definisce un provider di proprietà di Windows PowerShell che esegue operazioni sulle proprietà degli elementi nell'archivio dati. Nella tabella seguente sono elencati i cmdlet esposti da questa interfaccia.

> [!NOTE]
> Il parametro `Path` in questi cmdlet indica il percorso di un elemento anziché l'identificazione di una proprietà.

|        Cmdlet        |                                                                                   Definizione                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | Imposta le proprietà degli elementi specificati sul valore "Clear". Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.      |
| `Get-ItemProperty`   | Recupera le proprietà dagli elementi specificati e trasmette gli oggetti risultanti.                                                                                                |
| `Set-ItemProperty`   | Imposta le proprietà degli elementi specificati con i valori indicati. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`. |

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

L'interfaccia [System. Management. Automation. provider. Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) , derivata da [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definisce un provider che specifica i parametri dinamici per i cmdlet supportati. Questo tipo di provider gestisce le operazioni per le quali è possibile definire le proprietà in fase di esecuzione, ad esempio una nuova operazione della proprietà. Queste operazioni non sono possibili per gli elementi con proprietà definite in modo statico.
Nella tabella seguente sono elencati i cmdlet esposti da questa interfaccia.

|        Cmdlet         |                                                                                Definizione                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | Copia una proprietà dall'elemento specificato a un altro elemento. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`. |
| `Move-ItemProperty`   | Sposta una proprietà dall'elemento specificato a un altro elemento. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.  |
| `New-ItemProperty`    | Crea una proprietà sugli elementi specificati e trasmette gli oggetti risultanti.                                                                                             |
| `Remove-ItemProperty` | Rimuove una proprietà per gli elementi specificati.                                                                                                                              |
| `Rename-ItemProperty` | Rinomina una proprietà degli elementi specificati. Questo cmdlet non passa un oggetto di output attraverso la pipeline, a meno che non sia specificato il parametro `PassThru`.                 |

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

L'interfaccia [System. Management. Automation. provider. Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) aggiunge la funzionalità del descrittore di sicurezza a un provider. Questa interfaccia consente all'utente di ottenere e impostare le informazioni sul descrittore di sicurezza per un elemento nell'archivio dati. Nella tabella seguente sono elencati i cmdlet esposti da questa interfaccia.

|  Cmdlet   |                                                                                                                                                                                                          Definizione                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | Recupera le informazioni contenute in un elenco di controllo di accesso (ACL), che fa parte di un descrittore di sicurezza utilizzato per proteggere le risorse del sistema operativo, ad esempio un file o un oggetto.                                                                                                                                                                                                                                      |
| `Set-Acl` | Imposta le informazioni per un ACL. È nel formato di un'istanza di [System. Security. AccessControl. ObjectSecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) negli elementi designati per il percorso specificato. Questo cmdlet può impostare informazioni su file, chiavi e sottochiavi nel registro di sistema o qualsiasi altro elemento del provider se il provider di Windows PowerShell supporta l'impostazione delle informazioni di sicurezza. |

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Funzionamento di Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)