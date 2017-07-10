---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Applicazione delle configurazioni
ms.openlocfilehash: db82788650186eb82f67b30b24cd45b719bbe314
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="enacting-configurations" class="xliff"></a>
# Applicazione delle configurazioni

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Ci sono due modi per applicare le configurazioni di PowerShell DSC (Desired State Configuration): la modalità push e la modalità pull.

<a id="push-mode" class="xliff"></a>
## Modalità push

![Modalità push](images/Push.png "Come funziona la modalità push")

La modalità push fa riferimento a un utente che applica attivamente una configurazione in un nodo di destinazione chiamando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).

Dopo la creazione e la compilazione di una configurazione, è possibile applicarla in modalità push chiamando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), impostando il parametro -Path del cmdlet sul percorso in cui si trova il file MOF di configurazione. Se, ad esempio, il file MOF di configurazione si trova in `C:\DSC\Configurations\localhost.mof`, per applicarlo al computer locale usare il comando seguente: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Nota__: per impostazione predefinita, DSC esegue una configurazione come processo in background. Per eseguire la configurazione in modo interattivo, chiamare [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) con il parametro __-Wait__.


<a id="pull-mode" class="xliff"></a>
## Modalità pull

![Modalità pull](images/Pull.png "Come funziona la modalità pull")

In modalità pull, i client di pull sono configurati per ottenere le relative configurazioni DSC da un server di pull remoto. Analogamente, il server di pull è stato configurato per ospitare il servizio DSC e ne è stato effettuato il provisioning con le configurazioni e le risorse necessarie per i client di pull. Ogni client di pull ha un'attività pianificata che esegue un controllo di conformità periodico sulla configurazione del nodo. Quando l'evento viene generato per la prima volta, Gestione configurazione locale nel client di pull effettua una richiesta al server di pull per ottenere la configurazione specificata in Gestione configurazione locale. Se tale configurazione è disponibile nel server di pull e supera i controlli di convalida iniziali, viene trasmessa al client di pull, dove viene quindi eseguita da Gestione configurazione locale.

Gestione configurazione locale verifica che il client sia conforme alla configurazione a intervalli regolari, come specificato dalla proprietà **ConfigurationModeFrequencyMins** di Gestione configurazione locale. Gestione configurazione locale verifica se sono disponibili configurazioni aggiornate nel server di pull a intervalli regolari, come specificato dalla proprietà **RefreshModeFrequency** di Gestione configurazione locale. Per informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).

Per altre informazioni sulla configurazione di un server di pull DSC, vedere [Configurazione di un server di pull Web DSC](pullServer.md).

Se si preferisce usare un servizio online per ospitare la funzionalità del server di pull, vedere il servizio [Automation DSC per Azure](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/).

Gli argomenti seguenti illustrano come configurare i client e i server di pull:

- [Configurazione di un server di pull Web](pullServer.md)
- [Configurazione di un server di pull SMB](pullServerSMB.md)
- [Configurazione di un client di pull](pullClientConfigID.md)

