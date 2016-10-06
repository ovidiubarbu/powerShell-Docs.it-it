---
title: Gestione configurazione locale di Windows PowerShell 4.0 DSC (Desired State Configuration)
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 25195166f4d9dd668427d6bb5d748ef61273cdee

---

# Gestione configurazione locale di Windows PowerShell 4.0 DSC (Desired State Configuration)

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Gestione configurazione locale è il motore di Windows PowerShell DSC (Desired State Configuration). Viene eseguito in tutti i nodi di destinazione e ha la responsabilità di chiamare le risorse di configurazione incluse in uno script di configurazione DSC. Questo argomento contiene l'elenco delle proprietà di Gestione configurazione locale e descrive in che modo modificare le impostazioni di Gestione configurazione locale in un nodo di destinazione.

## Proprietà di Gestione configurazione locale
Di seguito sono elencate le proprietà di Gestione configurazione locale che è possibile impostare o recuperare.
 
* **AllowModuleOverwrite**: controlla se le nuove configurazioni scaricate dal server di configurazione possono sovrascrivere quelle meno recenti nel nodo di destinazione. I possibili valori sono True e False.
* **CertificateID**: GUID che specifica un certificato usato per proteggere le credenziali per l'accesso alla configurazione. Per altre informazioni, vedere [Protezione delle credenziali in Windows PowerShell DSC (Desired State Configuration)](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
* **ConfigurationID**: indica un GUID usato per ottenere un file di configurazione specifico da un server configurato come server di "pull". Il GUID garantisce l'accesso al file di configurazione corretto.
* **ConfigurationMode**: specifica il modo in cui Gestione configurazione locale applica effettivamente la configurazione ai nodi di destinazione. Può accettare i valori seguenti:
    - **ApplyOnly**: con questa opzione, DSC applica la configurazione e non esegue altre operazioni, a meno che non venga rilevata una nuova configurazione quando si invia una nuova configurazione direttamente al nodo di destinazione ("push") o se è stato configurato un server di "pull" e DSC individua una nuova configurazione quando controlla nel server di "pull". Se la configurazione del nodo di destinazione non è sincronizzata, non viene eseguita alcuna azione.
    - **ApplyAndMonitor**: con questa opzione (che è quella predefinita), DSC applica tutte le nuove configurazioni, sia quelle inviate direttamente al nodo di destinazione sia quelle individuate in un server di "pull". Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log. Per altre informazioni sulla registrazione di DSC, vedere la pagina sull'[uso di registri eventi per la diagnosi di errori in DSC (Desired State Configuration)](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
    - **ApplyAndAutoCorrect**: con questa opzione, DSC applica tutte le nuove configurazioni, sia quelle inviate direttamente al nodo di destinazione sia quelle individuate in un server di "pull". Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log e quindi tenta di modificare la configurazione del nodo di destinazione per garantire la conformità con il file di configurazione.
* **ConfigurationModeFrequencyMins**: rappresenta la frequenza (in minuti) con la quale l'applicazione in background di DSC tenta di implementare la configurazione corrente nel nodo di destinazione. Il valore predefinito è 15. Questo valore può essere impostato insieme a RefreshMode. Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il server di configurazione in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente. Indipendentemente dal valore di RefreshMode, il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins. La proprietà RefreshFrequencyMins deve essere impostata su un numero intero multiplo di ConfigurationModeFrequencyMins.
* **Credential**: indica le credenziali (come con Get-Credential) necessarie per accedere alle risorse remote, ad esempio per contattare il server di configurazione.
* **DownloadManagerCustomData**: rappresenta una matrice che contiene dati personalizzati specifici del gestore di download.
* **DownloadManagerName**: indica il nome del gestore di download di configurazioni e moduli.
* **RebootNodeIfNeeded**: alcune modifiche di configurazione in un nodo di destinazione possono richiedere il riavvio del nodo prima di avere effetto. Con il valore **True**, questa proprietà riavvia il nodo non appena la configurazione viene applicata completamente, senza altri avvisi. Se **False** (valore predefinito), la configurazione viene completata, ma il nodo deve essere riavviato manualmente perché le modifiche abbiano effetto.
* **RefreshFrequencyMins**: proprietà usata quando è stato configurato un server di "pull". Rappresenta la frequenza (in minuti) in base alla quale Gestione configurazione locale contatta un server di "pull" per scaricare la configurazione corrente. Questo valore può essere impostato insieme a ConfigurationModeFrequencyMins. Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il server di "pull" in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente. Il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins. Se la proprietà RefreshFrequencyMins non è impostata su un numero intero multiplo di ConfigurationModeFrequencyMins, il sistema arrotonda questo valore. Il valore predefinito è 30.
* **RefreshMode**: i possibili valori sono **Push** (predefinito) e **Pull**. Nella configurazione "push" è necessario inserire un file di configurazione in ogni nodo di destinazione, usando qualsiasi computer client. In modalità "pull" è necessario configurare un server di "pull" perché Gestione configurazione locale possa contattare i file di configurazione e accedervi.

### Esempio di aggiornamento delle impostazioni di Gestione configurazione locale

È possibile aggiornare le impostazioni di Gestione configurazione locale di un nodo di destinazione inserendo in uno script di configurazione un blocco **LocalConfigurationManager** all'interno del blocco del nodo, come mostrato nell'esempio seguente.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullServer/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"  
```

L'esecuzione dello script dell'esempio precedente genera un file MOF che specifica e archivia le impostazioni desiderate. Per applicare le impostazioni, è possibile usare il cmdlet **Set-DscLocalConfigurationManager**, come mostrato nell'esempio seguente.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Nota**: per il parametro **Path**, è necessario specificare lo stesso percorso specificato per il parametro **OutputPath** quando è stata richiamata la configurazione nell'esempio precedente.

Per visualizzare le impostazioni di Gestione configurazione locale correnti, è possibile usare il cmdlet **Get-DscLocalConfigurationManager**. Se richiamato senza parametri, per impostazione predefinita questo cmdlet ottiene le impostazioni di Gestione configurazione locale per il nodo in cui viene eseguito. Per specificare un altro nodo, usare il parametro **CimSession** con questo cmdlet.




<!--HONumber=Aug16_HO3-->


