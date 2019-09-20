---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Note sulla versione per WMF 5.x
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147581"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Note sulla versione di Windows Management Framework (WMF) 5.x

## <a name="wmf-50-changes"></a>Modifiche di WMF 5.0

- In PowerShell 5.0 è stato aggiunto un nuovo flusso di **informazioni** strutturato
- I miglioramenti di DSC includono quattro nuove risorse DSC:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Aggiunta della funzionalità JEA (Just Enough Administration) per consentire l'amministrazione basata su ruoli tramite la comunicazione remota di PowerShell
- PowerShell 5.0 estende il linguaggio in modo da includere le enumerazioni e le classi definiti dall'utente
- Miglioramento delle funzionalità di debug in PowerShell ISE e aggiunta del debug remoto
- Aggiunta dei moduli PowerShellGet e PackageManagement
- Miglioramento della registrazione e delle trascrizioni per gli script di PowerShell
- Aggiunta di cmdlet CMS (Cryptographic Message Syntax)
- WMF 5.0 include il modulo NetworkSwitchManager per Windows
- Aggiunta del modulo Microsoft.PowerShell.ODataUtils
- Aggiunta del supporto per Registrazione inventario software (SIL)
- Vari cmdlet nuovi o aggiornati in risposta alle richieste e alle segnalazioni di problemi degli utenti

## <a name="wmf-51-changes"></a>Modifiche di WMF 5.1

WMF 5.1 include i componenti PowerShell, WMI, WinRM e Registrazione inventario software (SIL) rilasciati con Windows Server 2016. WMF 5.1 può essere installato in Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e offre vari miglioramenti rispetto a WMF 5.0, tra cui:

- Nuovi cmdlet
- I miglioramenti apportati a PowerShellGet includono l'applicazione di moduli firmati e l'installazione di moduli JEA
- È stato aggiunto il supporto di PackageManagement per i contenitori, l'installazione di CBS, l'installazione basata su EXE e i pacchetti CAB
- Miglioramenti del debug per le classi DSC e PowerShell
- Miglioramenti relativi alla sicurezza, incluso quando si usano i cmdlet PowerShellGet e quando si applicano i moduli firmati da catalogo provenienti dal server di pull
- Risposte ad alcune richieste o problemi segnalati da utenti

> [!IMPORTANT]
> Prima di installare WMF 5.1 in Windows Server 2008 o Windows 7, verificare che WMF 3.0 non sia installato. Per altre informazioni, vedere [Prerequisiti di WMF 5.1 per Windows Server 2008 R2 SP1 e Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>Edizioni di PowerShell

A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

- **Desktop Edition:** si basa su .NET Framework e garantisce compatibilità con script e moduli destinati a versioni di PowerShell eseguiti in edizioni di Windows con footprint completo, ad esempio Server Core e Windows Desktop.
- **Core Edition:** si basa su .NET Core e garantisce compatibilità con script e moduli destinati a versioni di PowerShell eseguiti in edizioni di Windows con footprint ridotto, ad esempio Nano Server e Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Altre informazioni sull'uso delle edizioni di PowerShell

- [Determinare l'edizione di PowerShell in esecuzione con $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrare i risultati di Get-Module in base a CompatiblePSEditions con il parametro PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Impedire l'esecuzione di script a meno che non vengano eseguiti in un'edizione compatibile di PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Dichiarare la compatibilità di un modulo con versioni specifiche di PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Modulo Analysis Cache

A partire da WMF 5.1, PowerShell fornisce il controllo sul file che viene usato per memorizzare nella cache i dati relativi a un modulo, ad esempio i comandi esportati.

Per impostazione predefinita, questa cache è archiviata nel file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. La cache viene in genere letta all'avvio durante la ricerca di un comando e viene scritta in un thread in background ad un certo punto dopo l'importazione di un modulo.

Per modificare il percorso predefinito della cache, impostare la variabile di ambiente `$env:PSModuleAnalysisCachePath` prima di avviare PowerShell. Le modifiche apportate a questa variabile di ambiente influiranno solo sui processi figlio. Il valore deve denominare un percorso completo (nome di file incluso) per il quale PowerShell dispone dell'autorizzazione per creare e scrivere file. Per disabilitare la cache del file, impostare questo valore su un percorso non valido, ad esempio:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Questo imposta il percorso su un dispositivo non valido. Se PowerShell non riesce a scrivere nel percorso, non verrà restituito alcun errore. Sarà tuttavia possibile visualizzare una segnalazione errori mediante un'utilità di traccia:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Quando si scrive nella cache, PowerShell controllerà i moduli non più disponibili per evitare di aumentare inutilmente le dimensioni della cache. Talvolta questi controlli non sono consigliabili. In questo caso, è possibile disattivarli impostando:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

L'impostazione di questa variabile di ambiente avrà effetto immediato nel processo corrente.

## <a name="specifying-module-version"></a>Specifica della versione del modulo

In WMF 5.1 `using module` si comporta esattamente come altre costruzioni correlate ai moduli di PowerShell.
In precedenza, non era possibile specificare una versione particolare del modulo. Se erano presenti più versioni, veniva restituito un errore.

In WMF 5.1:

- È possibile usare il [costruttore ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

  Questa tabella hash ha lo stesso formato di `Get-Module -FullyQualifiedName`.

  **Esempio:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Se sono presenti più versioni del modulo, PowerShell usa la **stessa logica di risoluzione** di `Import-Module` e non restituisce un errore. Comportamento analogo a `Import-Module` e `Import-DscResource`.

## <a name="improvements-to-pester"></a>Miglioramenti a Pester

In WMF 5.1 la versione di Pester fornita con PowerShell è stata aggiornata dalla versione 3.3.5 alla 3.4.0.
Questo aggiornamento migliora il comportamento di Pester in Nano Server.

È possibile vedere le modifiche apportate per Pester esaminando il file [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) nel repository di GitHub.
