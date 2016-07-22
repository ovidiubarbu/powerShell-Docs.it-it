---
title: Miglioramenti di OneGet in WMF 5.1 (anteprima)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1d0bd545b52ef56045f2ec740b05c4e0fd93bb67

---

# Miglioramenti apportati a OneGet
WMF 5.1 include una serie di correzioni e miglioramenti per risolvere alcuni dei problemi rilevati dagli utenti della versione WMF 5.0. 

##Rimozione dell'alias della versione

**Scenario**: se si dispone delle versioni 1.0 e 2.0 di un pacchetto, P1, installate nel sistema e si vuole disinstallare la versione 1.0, è necessario eseguire "uninstall-package -name P1 -version 1.0" e attendere che la versione 1.0 venga disinstallata dopo l'esecuzione del cmdlet. Tuttavia, il risultato è che viene disinstallata la versione 2.0. 
    
Ciò si verifica perché il parametro "-version" è un alias del parametro "-minimumversion". Quando OneGet esegue la ricerca di un pacchetto qualificato con la versione minima 1.0, restituisce la versione più recente. Questo comportamento è previsto nei casi normali, perché trovare la versione più recente è in genere il risultato desiderato. Tuttavia, non dovrebbe applicarsi al caso di uninstall-package.
    
**Soluzione**: in WMF 5.1 l'alias -version viene rimosso completamente in OneGet e PowerShellGet. 

##Più richieste per l'avvio del provider NuGet

**Scenario**: quando si esegue Find-Module o Install-Module o altri cmdlet OneGet nel computer in uso per la prima volta, OneGet tenta di avviare il provider NuGet. Ciò avviene perché il provider PowerShellGet usa anche il provider NuGet per scaricare i moduli di PowerShell. OneGet quindi chiede all'utente l'autorizzazione per installare il provider NuGet. Dopo che l'utente seleziona "Sì" per l'avvio, verrà installata la versione più recente del provider NuGet. 
    
Tuttavia, in alcuni casi, quando si dispone di una versione precedente del provider NuGet installata nel computer in uso, in alcuni casi viene caricata per prima la versione precedente di NuGet nella sessione di PowerShell. Si tratta della race condition di OneGet. Tuttavia PowerShellGet richiede la versione più recente del provider NuGet, pertanto PowerShellGet chiede a OneGet di avviare nuovamente il provider NuGet. Ciò comporta l'esecuzione di più richieste di avvio del provider NuGet.

**Soluzione**: In WMF 5.1, OneGet carica la versione più recente del provider NuGet per evitare l'esecuzione di più richieste di avvio del provider NuGet.

È possibile aggirare il problema anche eliminando manualmente la versione precedente del provider NuGet (NuGet-Anycpu.exe), se presente, da $env:Programmi\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


##Supporto per OneGet nei computer solo con accesso Intranet

**Scenario**: In WMF 5.0, OneGet non supportava i computer che disponevano solo dell'accesso Intranet, ma non Internet.

**Soluzione**: In WMF 5.1, è possibile seguire questa procedura per consentire ai computer Intranet di usare OneGet:

1. Scaricare il provider NuGet usando un altro computer che dispone di una connessione Internet tramite Install-PackageProvider NuGet.

2. Trovare il provider NuGet in $env:Programmi\PackageManagement\ProviderAssemblies\nuget o $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copiare i file binari in una cartella o in una condivisione di rete a cui il computer Intranet può accedere e quindi installare il provider NuGet con "Install-PackageProvider NuGet -Source <Path to folder>".


##Miglioramenti apportati alla registrazione di eventi

Quando si installano i pacchetti, si modifica lo stato del computer. In WMF 5.1, OneGet registra gli eventi nel registro eventi di Windows per installare, disinstallare e salvare le attività del pacchetto. Il canale dell'evento è identico a quello di PowerShell, ovvero Microsoft-Windows-PowerShell/Operational.

##Supporto per l'autenticazione di base

In WMF 5.1, OneGet supporta la ricerca e l'installazione dei pacchetti da un repository che richiede l'autenticazione di base. È possibile fornire le credenziali ai cmdlet Find-Package e Install-Package. Ad esempio:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
##Supporto per l'uso di OneGet protetto da un proxy

In WMF 5.1, OneGet accetta ora nuovi parametri proxy: -ProxyCredential e -Proxy. Grazie a questi parametri è possibile specificare le credenziali e l'URL del proxy nei cmdlet di OneGet. Per impostazione predefinita, vengono usate le impostazioni proxy del sistema. Ad esempio:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


