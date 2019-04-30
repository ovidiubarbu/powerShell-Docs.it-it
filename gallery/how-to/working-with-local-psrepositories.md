---
ms.date: 11/06/2018
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: Uso dei repository PowerShell locali
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084097"
---
# <a name="working-with-local-powershellget-repositories"></a>Uso dei repository PowerShellGet locali

Il modulo PowerShellGet supporta repository diversi da PowerShell Gallery.
Questi cmdlet consentono gli scenari seguenti:

- Supporto di un set attendibile e pre-convalidato di moduli PowerShell per l'uso nell'ambiente
- Test di una pipeline CI/CD che compila moduli o script PowerShell
- Distribuzione di moduli e script PowerShell in sistemi che non possono accedere a Internet

Questo articolo descrive come configurare un repository PowerShell locale. L'articolo riguarda anche il modulo [OfflinePowerShellGetDeploy][] disponibile in PowerShell Gallery. Questo modulo contiene i cmdlet per installare la versione più recente di PowerShellGet nel repository locale.

## <a name="local-repository-types"></a>Tipi di repository locali

È possibile creare un repository PowerShell in due modi: Server NuGet o condivisione file. Ogni tipo presenta vantaggi e svantaggi.

Server NuGet

| Vantaggi| Svantaggi |
| --- | --- |
| Simula quasi perfettamente la funzionalità di PowerShell Gallery | L'app a più livelli richiede la pianificazione e il supporto delle operazioni |
| NuGet si integra con Visual Studio e altri strumenti | È necessario gestire il modello di autenticazione e gli account NuGet |
| NuGet supporta i metadati in pacchetti `.Nupkg` | La pubblicazione richiede la gestione e la manutenzione delle chiavi API |
| Fornisce ricerca, amministrazione dei pacchetti e così via. | |

Condivisione file

| Vantaggi| Svantaggi |
| --- | --- |
| Semplice da configurare, sottoporre a backup e gestire | I metadati usati da PowerShellGet non sono disponibili |
| Modello di sicurezza semplice, autorizzazioni utente sulla condivisione | Nessuna interfaccia utente oltre la condivisione file di base |
| Nessun vincolo, ad esempio la sostituzione degli elementi esistenti | Sicurezza limitata e nessuna registrazione degli utenti e degli aggiornamenti che eseguono |

PowerShellGet è compatibile con entrambi i tipi e supporta l'individuazione delle versioni e l'installazione delle dipendenze.
Tuttavia, alcune funzionalità compatibili con PowerShell Gallery non sono disponibili per le condivisioni file o i server NuGet di base.

- Tutti gli elementi sono costituiti da pacchetti, senza distinzione tra script, moduli, risorse DSC o funzionalità di ruoli.
- I server di condivisione file non possono visualizzare i metadati del pacchetto, inclusi i tag.

## <a name="creating-a-local-repository"></a>Creazione di un repository locale

L'articolo seguente elenca i passaggi per la configurazione di un server NuGet personalizzato.

- [NuGet.Server][]

Seguire i passaggi fino al momento dell'aggiunta di pacchetti. I passaggi per la [pubblicazione di un pacchetto](#publishing-to-a-local-repository) sono trattati più avanti in questo articolo.

Per un repository basato su condivisione file, assicurarsi che gli utenti dispongano delle autorizzazioni per accedere alla condivisione file.

## <a name="registering-a-local-repository"></a>Registrazione di un repository locale

Prima di poter usare un repository, è necessario registrarlo con il comando `Register-PSRepository`.
Negli esempi seguenti, **InstallationPolicy** è impostato su *Trusted*, presupponendo che si ritenga attendibile il repository.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Notare la differenza nel modo in cui i due comandi gestiscono **ScriptSourceLocation**. Per repository basati su condivisione file, **SourceLocation** e **ScriptSourceLocation** devono corrispondere. Per un repository basato sul Web, devono essere diversi, quindi in questo esempio viene aggiunto un carattere "/" finale a **SourceLocation**.

Se si intende rendere predefinito il repository PowerShell appena creato, è necessario annullare la registrazione di tutti gli altri repository PowerShell. Ad esempio:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Il nome di repository 'PSGallery' è riservato per l'uso da parte di PowerShell Gallery. È possibile annullare la registrazione di PSGallery, ma non è possibile riutilizzare il nome PSGallery per un altro repository.

Se è necessario ripristinare PSGallery, eseguire il comando seguente:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Pubblicazione in un repository locale

Dopo aver registrato il repository PowerShell locale, sarà possibile eseguire pubblicazioni al suo interno. Esistono due scenari di pubblicazione principali: pubblicazione del proprio modulo e pubblicazione di un modulo da PSGallery.

### <a name="publishing-a-module-you-authored"></a>Pubblicazione di un modulo creato dall'utente

Usare `Publish-Module` e `Publish-Script` per pubblicare un modulo nel repository PowerShell locale con la stessa procedura valida per PowerShell Gallery.

- Specificare la posizione per il codice
- Specificare una chiave API
- Specificare il nome del repository. Ad esempio, `-PSRepository LocalPSRepo`

> [!NOTE]
> È necessario creare un account nel server NuGet, quindi eseguire l'accesso per generare e salvare la chiave API.
> Per una condivisione file, usare una stringa non vuota per il valore NuGetApiKey.

Di seguito sono riportati alcuni esempi.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script. Usare un sistema di gestione delle chiavi sicuro.

### <a name="publishing-a-module-from-the-psgallery"></a>Pubblicazione di un modulo da PSGallery

Per pubblicare un modulo da PSGallery nel repository PowerShell locale, è possibile usare il cmdlet 'Save-Package'.

- Specificare il nome del pacchetto
- Specificare 'NuGet' come provider
- Specificare la posizione di PSGallery come origine (https://www.powershellgallery.com/api/v2)
- Specificare il percorso del repository locale

Esempio:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Se il repository PowerShell locale è basato sul Web, è necessario un passaggio aggiuntivo che preveda l'uso di nuget.exe per eseguire la pubblicazione.

Vedere la documentazione per l'uso di [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installazione di PowerShellGet in un sistema disconnesso

La distribuzione di PowerShellGet è difficile in ambienti che richiedono sistemi disconnessi da Internet. PowerShellGet include un processo bootstrap che installa la versione più recente al primo utilizzo. Il modulo OfflinePowerShellGetDeploy in PowerShell Gallery include cmdlet che supportano questo processo di bootstrap.

Per eseguire il bootstrap di una distribuzione offline, è necessario:

- Scaricare e installare OfflinePowerShellGetDeploy nel sistema connesso a Internet e nei sistemi disconnessi
- Scaricare PowerShellGet e le relative dipendenze nel sistema connesso a Internet usando i cmdlet `Save-PowerShellGetForOffline`
- Copiare PowerShellGet e le relative dipendenze dal sistema connesso a Internet al sistema disconnesso
- Usare `Install-PowerShellGetOffline` nel sistema disconnesso per posizionare PowerShellGet e le relative dipendenze nelle cartelle appropriate

I comandi seguenti usano `Save-PowerShellGetForOffline` per inserire tutti i componenti in una cartella `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

A questo punto, è necessario rendere il contenuto di `F:\OfflinePowerShellGet` disponibile per i sistemi disconnessi. Eseguire il cmdlet `Install-PowerShellGetOffline` per installare PowerShellGet nel sistema disconnesso.

> [!NOTE]
> È importante non eseguire PowerShellGet nella sessione di PowerShell prima di eseguire questi comandi. Una volta caricato PowerShellGet nella sessione, non sarà possibile aggiornare i componenti. Se si avvia PowerShellGet per errore, chiuderlo e riavviarlo.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Dopo aver eseguito questi comandi, sarà possibile pubblicare PowerShellGet nel repository locale.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script. Usare un sistema di gestione delle chiavi sicuro.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
