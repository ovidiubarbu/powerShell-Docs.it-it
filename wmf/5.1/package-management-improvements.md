---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
contributor: jianyunt, quoctruong
title: Miglioramenti della gestione pacchetti in WMF 5.1
ms.openlocfilehash: adcddcc94022f4961f3dd23c2cd56f2a8720049b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682562"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Miglioramenti della gestione pacchetti in WMF 5.1#

## <a name="improvements-in-packagemanagement"></a>Miglioramenti appartati a Gestione pacchetti ##
Di seguito vengono descritte le correzioni apportate in WMF 5.1:

### <a name="version-alias"></a>Alias della versione

**Scenario**: se si dispone delle versioni 1.0 e 2.0 di un pacchetto, P1, installate nel sistema e si vuole disinstallare la versione 1.0, è necessario eseguire `Uninstall-Package -Name P1 -Version 1.0` e attendere che la versione 1.0 venga disinstallata dopo l'esecuzione del cmdlet. Tuttavia, il risultato è che viene disinstallata la versione 2.0.

Ciò si verifica perché il parametro `-Version` è un alias del parametro `-MinimumVersion`. Quando PackageManagement esegue la ricerca di un pacchetto qualificato con la versione minima 1.0, restituisce la versione più recente. Questo comportamento è previsto nei casi normali, perché trovare la versione più recente è in genere il risultato desiderato. Tuttavia, non dovrebbe applicarsi al caso di `Uninstall-Package`.

**Soluzione**: rimozione completa dell'alias `-Version` in PackageManagement (noto anche come OneGet) e PowerShellGet.

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Più richieste per l'avvio del provider NuGet

**Scenario**: Quando si esegue `Find-Module` o `Install-Module` o altri cmdlet PackageManagement nel computer per la prima volta, PackageManagement tenta di avviare il provider NuGet. Ciò avviene perché il provider PowerShellGet usa anche il provider NuGet per scaricare i moduli di PowerShell. PackageManagement quindi chiede all'utente l'autorizzazione per installare il provider NuGet. Dopo che l'utente seleziona "Sì" per l'avvio, verrà installata la versione più recente del provider NuGet.

Se tuttavia si dispone di una versione precedente del provider NuGet installata nel computer in uso, in alcuni casi viene caricata per prima la versione precedente di NuGet nella sessione di PowerShell. Si tratta della race condition di PackageManagement. PowerShellGet richiede tuttavia la versione più recente del provider NuGet, pertanto PowerShellGet chiede a PackageManagement di avviare nuovamente il provider NuGet. Ciò comporta l'esecuzione di più richieste di avvio del provider NuGet.

**Soluzione**: In WMF 5.1, PackageManagement carica la versione più recente del provider NuGet per evitare più richieste di avvio del provider NuGet.

È possibile aggirare il problema anche eliminando manualmente la versione precedente del provider NuGet (NuGet-Anycpu.exe), se presente, da $env:Programmi\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Supporto per PackageManagement nei computer solo con accesso Intranet

**Scenario**: Per lo scenario aziendale, gli utenti operano in un ambiente in cui è presente alcun accesso a Internet ma Intranet solo. In WMF 5.0, PackageManagement non supporta questo caso.

**Scenario**: In WMF 5.0, PackageManagement non supporta computer che dispongono solo Intranet, ma non Internet, l'accesso.

**Soluzione**: In WMF 5.1, è possibile seguire questa procedura per consentire ai computer Intranet di usare PackageManagement:

1. Scaricare il provider NuGet usando un altro computer che dispone di una connessione Internet tramite `Install-PackageProvider -Name NuGet`.

2. Trovare il provider NuGet sotto `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget`  o  `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copiare i file binari in una cartella o in una condivisione di rete a cui il computer Intranet può accedere e quindi installare il provider NuGet con `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Miglioramenti apportati alla registrazione di eventi

Quando si installano i pacchetti, si modifica lo stato del computer. In WMF 5.1, PackageManagement ora registra gli eventi nel registro eventi di Windows per le attività `Install-Package`, `Uninstall-Package` e `Save-Package`. Il registro eventi è identico a quello di PowerShell, vale a dire `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Supporto per l'autenticazione di base

In WMF 5.1, PackageManagement supporta la ricerca e l'installazione dei pacchetti da un repository che richiede l'autenticazione di base. È possibile fornire le credenziali per i cmdlet `Find-Package` e `Install-Package`. Ad esempio:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Supporto per l'utilizzo di PackageManagement dietro un proxy

In WMF 5.1, PackageManagement accetta ora i nuovi parametri proxy `-ProxyCredential` e `-Proxy`. Grazie a questi parametri è possibile specificare le credenziali e l'URL del proxy nei cmdlet di PackageManagement. Per impostazione predefinita, vengono usate le impostazioni proxy del sistema. Ad esempio:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
