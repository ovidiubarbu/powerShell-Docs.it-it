---
title: Miglioramenti apportati a PackageManagement (OneGet)
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 4c1b57f221d0f502313eecb21dd36b5e85c2de4d
ms.openlocfilehash: e2646a59c7a241491ef934c62fdfb6d649d16191

---

>Nota: specificare una proposta di titolo descrittivo e una breve descrizione

## Miglioramenti apportati a PackageManagement (OneGet) ##
Di seguito sono illustrate le correzioni apportate in WMF 5.1 per risolvere alcuni dei problemi riscontrati dagli utenti nella versione WMF 5.0. 

1 **Alias della versione**

**Scenario**: se si dispone delle versioni 1.0 e 2.0 di un pacchetto, P1, installate nel sistema e si vuole disinstallare la versione 1.0, è necessario eseguire "uninstall-package -name P1 -version 1.0". Si prevede che la versione 1.0 venga disinstallata dopo l'esecuzione del cmdlet. Tuttavia, il risultato è che viene disinstallata la versione 2.0. 
    
La causa di questo problema è che il parametro "-version" è un alias del parametro "-minimumversion". Quando OneGet esegue la ricerca di un pacchetto qualificato con la versione minima 1.0, restituisce la versione più recente. Questo comportamento è previsto nei casi normali, perché trovare la versione più recente è in genere il risultato desiderato dalla maggior parte degli utenti. Tuttavia, non dovrebbe applicarsi al caso di uninstall-package.
    
**Soluzione**: -version è stato rimosso completamente in OneGet e PowerShellGet. 

2 **Più richieste per l'avvio del provider NuGet**

**Scenario**: quando si esegue Find-Module o Install-Module o altri cmdlet OneGet nel computer in uso per la prima volta, OneGet tenta di avviare il provider NuGet. Ciò avviene perché il provider PowerShellGet usa anche il provider NuGet per scaricare i moduli di PowerShell. OneGet quindi chiede all'utente l'autorizzazione per installare il provider NuGet. Dopo che l'utente seleziona "Sì" per l'avvio, verrà installata la versione più recente del provider NuGet. 
    
Tuttavia, se si dispone di una versione precedente del provider NuGet installata nel computer in uso, in alcuni casi viene caricata per prima la versione precedente di NuGet nella sessione di PowerShell. Si tratta della race condition di OneGet. Tuttavia PowerShellGet richiede la versione più recente del provider NuGet, pertanto PowerShellGet chiede a OneGet di avviare nuovamente il provider NuGet. Per questo motivo vengono eseguite più richieste di avvio del provider NuGet.

**Soluzione**: OneGet ora carica la versione più recente del provider NuGet per evitare l'esecuzione di più richieste di avvio del provider NuGet.

Una soluzione alternativa consiste nell'eliminazione manuale della versione precedente del provider NuGet (NuGet-Anycpu.exe), se presente, da $env:Programmi\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


3 **Computer con solo accesso Intranet**

**Scenario**: in uno scenario aziendale gli utenti operano in un ambiente in cui non è presente alcun accesso Internet, ma solo Intranet. In WMF 5.0, OneGet non supportava questo caso.

**Soluzione**:
- è possibile scaricare il provider NuGet usando un altro computer con connessione Internet tramite il comando Install-PackageProvider NuGet.

- Trovare il provider NuGet in $env:Programmi\PackageManagement\ProviderAssemblies\nuget o $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

- Copiare i file binari in una cartella o in una condivisione di rete a cui il computer (quello senza Internet) ha accesso troppo accedere e installare il provider NuGet con "Install-PackageProvider NuGet -Source <Path to folder>".


4 **Registro eventi**

Quando si installano i pacchetti, si modifica lo stato del computer in uso. A scopo di analisi, OneGet registra gli eventi nel registro eventi di Windows per installare, disinstallare e salvare il pacchetto. Il canale dell'evento è identico a quello di PowerShell, ovvero Microsoft-Windows-PowerShell/Operational.

5 **Supporto dell'autenticazione** OneGet supporta ora la ricerca e l'installazione dei pacchetti da un repository che richiede l'autenticazione di base. È possibile fornire le credenziali ai cmdlet Find-Package e Install-Package. Ad esempio:
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **Uso di OneGet protetto da un proxy**

OneGet accetta ora nuovi parametri proxy: -ProxyCredential e -Proxy. Grazie a questi parametri è possibile specificare le credenziali e l'URL del proxy nei cmdlet di OneGet. Per impostazione predefinita, vengono usate le impostazioni proxy del sistema. Ad esempio:
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


