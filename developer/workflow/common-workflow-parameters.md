---
title: Parametri comuni del flusso di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080408"
---
# <a name="common-workflow-parameters"></a>Parametri comuni del flusso di lavoro

Un'attività flusso di lavoro generata da un cmdlet di Windows PowerShell definisce vari parametri che comuni a tutte le attività. È possibile specificare un subset di questi parametri in fase di creazione in modo che gli autori del flusso di lavoro è possono personalizzare le attività. Un altro sottogruppo di questi parametri può essere specificato dall'utente quando si chiama l'attività.

Parametri comuni del flusso di lavoro sono raggruppati in diverse categorie come indicato di seguito.

## <a name="connectivity-parameters"></a>Parametri di connettività

|Nome|Tipo|Description|Può essere specificato dall'utente finale in fase di esecuzione?|Può essere specificato dall'autore del flusso di lavoro in fase di creazione?|Può essere specificato dall'autore del flusso di lavoro per la creazione di istanze?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Un elenco di nomi di computer per cui si desidera avviare i processi.|Sì|Yes|Sì|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Le credenziali di autenticazione da usare per l'accesso al computer specificato dal parametro PSComputerName. Questo parametro è valido solo se viene specificato PSComputerName.|Sì|Yes|Sì|
|PSPort|UInt32|La porta da utilizzare per l'esecuzione del flusso di lavoro.|Sì|Yes|Sì|
|PSUseSSL|Booleano|Usare il protocollo di sicuro Sockets Layer (SSL) per stabilire una connessione sicura al computer remoto per l'esecuzione del flusso di lavoro.|Sì|Yes|Sì|
|PSConfigurationName|String|La configurazione di sessione utilizzata per eseguire il flusso di lavoro.|Sì|Yes|Sì|
|PSApplicationName|String|Parte relativa al nome dell'applicazione dell'URI di connessione per l'esecuzione del flusso di lavoro. Usare questo parametro solo quando non si usa il parametro ConnectionURI.|Sì|Yes|Sì|
|PSThrottleLimit|UInt32|Il numero massimo di connessioni simultanee che possono essere stabilite per l'esecuzione del flusso di lavoro.|Sì|TBD|Sì|
|PSConnectionURI|String[]|Matrice di URI completo che specificano gli endpoint per le sessioni interattive utilizzate per eseguire il flusso di lavoro.|Sì|Yes|Sì|
|PSAllowRedirection|Booleano|Specifica se consentire il reindirizzamento della connessione a un URI alternativo per l'esecuzione del flusso di lavoro.|Sì|Yes|Sì|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Opzioni avanzate per la sessione utilizzata per eseguire il flusso di lavoro.|Sì|Yes|Sì|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Valore di [System](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) enumerazione che specifica il meccanismo di autenticazione usato per autenticare le credenziali dell'utente.|Sì|Yes|Sì|
|PSCertificateThumbprint|String|Il digitale certificato di chiave pubblica (X509) di un account utente che dispone dell'autorizzazione per l'esecuzione del flusso di lavoro.|Sì|Yes|Sì|

### <a name="behavior-parameters"></a>Parametri di comportamento