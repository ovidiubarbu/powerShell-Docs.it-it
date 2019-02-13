---
ms.date: 11/06/2018
contributor: JKeithB
keywords: raccolta,powershell,cmdlet,psgallery, psget
title: Utilizzo di PSRepositories locale
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682672"
---
# <a name="working-with-local-powershellget-repositories"></a>Uso dei repository PowerShellGet locali

I repository di supporto di modulo PowerShellGet diverso da PowerShell Gallery.
Questi cmdlet consentono gli scenari seguenti:

- Supportano un set affidabile e pre-convalidato dei moduli di PowerShell per l'uso nell'ambiente in uso
- Una pipeline CI/CD che compila i moduli di PowerShell o script di test
- Distribuire moduli e script di PowerShell per i sistemi che non è possibile accedere a internet

Questo articolo descrive come configurare un repository di PowerShell locale. L'articolo riguarda anche il [OfflinePowerShellGetDeploy][] modulo da PowerShell Gallery. Questo modulo contiene i cmdlet per installare la versione più recente di PowerShellGet nel repository locale.

## <a name="local-repository-types"></a>Tipi di repository locale

Esistono due modi per creare un PSRepository locale: Condivisione di file o server NuGet. Ogni tipo presenta vantaggi e svantaggi:

Server NuGet

| Vantaggi| Svantaggi |
| --- | --- |
| Simula strettamente la funzionalità di PowerShell Gallery | App a più livelli richiede operazioni di pianificazione e supporto |
| NuGet si integra con Visual Studio, altri strumenti | Modello di autenticazione e gestione degli account NuGet necessita |
| NuGet supporta i metadati in `.Nupkg` pacchetti | La pubblicazione richiede la manutenzione e gestione delle chiavi API |
| Offre ricerca amministrazione dei pacchetti, e così via. | |

Condivisione file

| Vantaggi| Svantaggi |
| --- | --- |
| Facile da configurare, eseguire il backup e gestire | I metadati utilizzati da PowerShellGet non sono disponibili |
| Modello di sicurezza semplice - le autorizzazioni utente per la condivisione | Nessuna interfaccia utente di là di condivisione file di base |
| Senza vincoli, ad esempio sostituendo gli elementi esistenti | Nessuna registrazione di chi Aggiorna cosa e sicurezza limitata |

PowerShellGet funziona con tipo e supporta l'individuazione delle versioni e installazione delle dipendenze.
Tuttavia, alcune funzionalità che funzionano per PowerShell Gallery non sono disponibili per i server NuGet base o le condivisioni file.

- Tutto ciò che è un pacchetto - alcuna differenza di script, moduli, risorse DSC o le funzionalità del ruolo.
- Condivisione di file server non possono visualizzare i metadati del pacchetto, inclusi tag.

## <a name="creating-a-local-repository"></a>Creazione di un repository locale

L'articolo seguente elenca i passaggi per la configurazione di NuGet Server personalizzato.

- [NuGet.Server][]

Seguire i passaggi fino al momento dell'aggiunta di pacchetti. I passaggi per la [pubblicazione di un pacchetto](#publishing-to-a-local-repository) sono trattati più avanti in questo articolo.

Per un repository basato su condivisione file, assicurarsi che gli utenti dispongano delle autorizzazioni per accedere alla condivisione file.

## <a name="registering-a-local-repository"></a>La registrazione di un repository locale

Prima di poter usare un repository, è necessario registrarlo con il `Register-PSRepository` comando.
Negli esempi seguenti, il **InstallationPolicy** è impostata su *attendibile*, presupponendo che si ritiene attendibile il proprio repository.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Prendere nota della differenza tra in che modo i due comandi gestiscono **ScriptSourceLocation**. Per un repository basato su condivisione file, il **SourceLocation** e **ScriptSourceLocation** devono corrispondere. Per un repository basato sul web, deve essere diversi, quindi in questo esempio una parentesi finale "/" viene aggiunto per il **SourceLocation**.

Se si desidera PSRepository appena creato sia il repository predefinito, è necessario annullare la registrazione di tutte le altre PSRepositories. Ad esempio:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Il nome del repository 'PSGallery' è riservato per l'uso da PowerShell Gallery. È possibile annullare la registrazione PSGallery, ma non è possibile riutilizzare il nome PSGallery per un altro repository.

Se si vuole ripristinare PSGallery, eseguire il comando seguente:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Pubblicazione in un repository locale

Dopo aver registrato PSRepository locale, è possibile pubblicare nel PSRepository locale. Esistono due scenari principali di pubblicazione: il proprio modulo di pubblicazione e pubblicazione di un modulo da PSGallery.

### <a name="publishing-a-module-you-authored"></a>Pubblicazione di un modulo che è stato creato

Uso `Publish-Module` e `Publish-Script` per pubblicare un modulo di PSRepository locale la stessa procedura valida per PowerShell Gallery.

- Specificare il percorso per il codice
- Specificare una chiave API
- Specificare il nome del repository. Ad esempio, `-PSRepository LocalPSRepo`

> [!NOTE]
> È necessario creare un account nel server NuGet, quindi accedi per generare e salvare la chiave API.
> Per una condivisione file, utilizzare qualsiasi stringa non vuota per il valore di chiave NuGetApiKey.

Di seguito sono riportati alcuni esempi.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script. Usare un sistema di gestione sicura delle chiavi.

### <a name="publishing-a-module-from-the-psgallery"></a>Pubblicazione di un modulo da PSGallery

Per pubblicare un modulo da PSGallery il PSRepository locale, è possibile usare il cmdlet 'Save-Package'.

- Specificare il nome del pacchetto
- Specificare 'NuGet' come il Provider
- Specificare il percorso PSGallery come il (di origine https://www.powershellgallery.com/api/v2)
- Specificare il percorso nel repository locale

Esempio:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Se il PSRepository locale è basata sul web, è necessaria un passaggio aggiuntivo che usa nuget.exe da pubblicare.

Vedere la documentazione per l'utilizzo [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Installazione PowerShellGet su un sistema disconnesso

Distribuzione di PowerShellGet è difficile in ambienti che richiedono i sistemi per essere disconnesso da internet. PowerShellGet è disponibile un processo bootstrap che installa la prima volta che viene usata la versione più recente. Il modulo OfflinePowerShellGetDeploy in PowerShell Gallery include cmdlet che supportano questo processo di bootstrap.

Per avviare una distribuzione non in linea, è necessario:

- Scaricare e installare il sistema OfflinePowerShellGetDeploy la connessione a internet e i sistemi disconnessi
- Download di PowerShellGet e le relative dipendenze nel sistema connesso a internet usando i `Save-PowerShellGetForOffline` cmdlet
- Copiare PowerShellGet e le relative dipendenze dal sistema connesso a internet nel disconnesso System
- Usare il `Install-PowerShellGetOffline` nel disconnesso sistema inserisca PowerShellGet e le relative dipendenze nelle cartelle appropriate

I comandi seguenti usano `Save-PowerShellGetForOffline` inserire tutti i componenti in una cartella `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

A questo punto, è necessario rendere il contenuto di `F:\OfflinePowerShellGet` disponibile per i sistemi disconnessi. Eseguire il `Install-PowerShellGetOffline` cmdlet per installare PowerShellGet nel disconnesso sistema.

> [!NOTE]
> È importante che non è eseguito PowerShellGet nella sessione di PowerShell prima di eseguire questi comandi. Una volta PowerShellGet è caricato nella sessione, non è possibile aggiornare i componenti. Se si avvia PowerShellGet per errore, chiudere e riavviare PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Dopo aver eseguito questi comandi, si è pronti a pubblicare PowerShellGet nel repository locale.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Per garantire la sicurezza, le chiavi API non devono essere hardcoded negli script. Usare un sistema di gestione sicura delle chiavi.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
