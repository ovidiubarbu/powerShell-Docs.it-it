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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366050"
---
# <a name="common-workflow-parameters"></a>Parametri comuni del flusso di lavoro

Un'attività del flusso di lavoro generata da un cmdlet di Windows PowerShell definisce un numero di parametri comuni a tutte le attività. Un subset di questi parametri può essere specificato in fase di creazione, in modo che gli autori del flusso di lavoro possano personalizzare le attività. Un altro subset di questi parametri può essere specificato dall'utente quando viene chiamata l'attività.

I parametri comuni del flusso di lavoro sono raggruppati in diverse categorie, come indicato di seguito.

## <a name="connectivity-parameters"></a>Parametri di connettività

|Name|Type|Description|Può essere specificato dall'utente finale in fase di esecuzione?|Può essere specificato dall'autore del flusso di lavoro in fase di creazione?|È possibile specificare l'autore del flusso di lavoro durante la creazione di istanze?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Elenco di nomi di computer per i quali avviare i processi.|Yes|Yes|Yes|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Credenziali di autenticazione da utilizzare per l'accesso ai computer specificati dal parametro PSComputerName. Questo parametro è valido solo se è specificato PSComputerName.|Yes|Yes|Yes|
|PSPort|UInt32|Porta da utilizzare per eseguire il flusso di lavoro.|Yes|Yes|Yes|
|PSUseSSL|Booleano|Usare il protocollo Secure Sockets Layer (SSL) per stabilire una connessione sicura al computer remoto per eseguire il flusso di lavoro.|Yes|Yes|Yes|
|PSConfigurationName|String|Configurazione di sessione utilizzata per eseguire il flusso di lavoro.|Yes|Yes|Yes|
|PSApplicationName|String|Parte relativa al nome dell'applicazione dell'URI di connessione per l'esecuzione del flusso di lavoro. Usare questo parametro solo quando non si usa il parametro ConnectionURI.|Yes|Yes|Yes|
|PSThrottleLimit|UInt32|Numero massimo di connessioni simultanee che è possibile stabilire per eseguire il flusso di lavoro.|Yes|TBD|Yes|
|PSConnectionURI|String[]|Matrice di URI completi che specificano gli endpoint per le sessioni interattive utilizzate per eseguire il flusso di lavoro.|Yes|Yes|Yes|
|PSAllowRedirection|Booleano|Specifica se consentire il reindirizzamento della connessione a un URI alternativo per eseguire il flusso di lavoro.|Yes|Yes|Yes|
|PSSessionOption|[System. Management. Automation. Remoting. PSSessionOption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Opzioni avanzate per la sessione utilizzata per eseguire il flusso di lavoro.|Yes|Yes|Yes|
|PSAuthentication|[System. Management. Automation. Runspaces. AuthenticationMechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Valore dell'enumerazione [System. Management. Automation. Runspaces. AuthenticationMechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) che specifica il meccanismo di autenticazione usato per autenticare le credenziali dell'utente.|Yes|Yes|Yes|
|PSCertificateThumbprint|String|Il certificato di chiave pubblica digitale (X509) di un account utente che dispone dell'autorizzazione per eseguire il flusso di lavoro.|Yes|Yes|Yes|

### <a name="behavior-parameters"></a>Parametri di comportamento