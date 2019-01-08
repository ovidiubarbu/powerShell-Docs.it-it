---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di Gestione configurazione locale nelle versioni precedenti di Windows PowerShell
ms.openlocfilehash: 31ba2ecdaa5a2ff7fcfddb1791c4d00343f4b5d5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401465"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Configurazione di Gestione configurazione locale nelle versioni precedenti di Windows PowerShell

>Si applica a: Windows PowerShell 4.0

**Per informazioni correlate a Windows PowerShell 5.0 e versioni successive, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).**

Gestione configurazione locale è il motore di Windows PowerShell DSC (Desired State Configuration).
Viene eseguito in tutti i nodi di destinazione e ha la responsabilità di chiamare le risorse di configurazione incluse in uno script di configurazione DSC.
Questo argomento contiene l'elenco delle proprietà di Gestione configurazione locale e descrive in che modo modificare le impostazioni di Gestione configurazione locale in un nodo di destinazione.

## <a name="local-configuration-manager-properties"></a>Proprietà di Gestione configurazione locale

Di seguito sono elencate le proprietà di Gestione configurazione locale che è possibile impostare o recuperare.

- AllowModuleOverwrite Controlla se le nuove configurazioni scaricate dal servizio di configurazione possono sovrascrivere quelle meno recenti nel nodo di destinazione. I possibili valori sono True e False.
- **CertificateID**: Identificazione personale di un certificato usato per credenziali protette passate in una configurazione. Per altre informazioni, vedere [Protezione delle credenziali in Windows PowerShell DSC (Desired State Configuration)](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- ConfigurationID Indica un GUID che consente di ottenere un file di configurazione specifico da un servizio di pull. Il GUID garantisce l'accesso al file di configurazione corretto.
- ConfigurationMode Specifica la modalità di Gestione configurazione locale applica effettivamente la configurazione ai nodi di destinazione. Può accettare i valori seguenti:
  - **ApplyOnly**: con questa opzione, DSC applica la configurazione e non esegue altre operazioni, a meno che non venga rilevata una nuova configurazione quando si invia una nuova configurazione direttamente al nodo di destinazione o se ci si connette a un servizio di pull e DSC individua una nuova configurazione quando controlla nel servizio di pull. Se la configurazione del nodo di destinazione non è sincronizzata, non viene eseguita alcuna azione.
  - ApplyAndMonitor Con questa opzione, ovvero l'impostazione predefinita, DSC applica tutte le nuove configurazioni, sia inviate direttamente al nodo di destinazione o il rilevamento in un servizio di pull. Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log. Per altre informazioni sulla registrazione di DSC, vedere la pagina sull'[uso di registri eventi per la diagnosi di errori in DSC (Desired State Configuration)](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - ApplyAndAutoCorrect Con questa opzione, DSC applica tutte le nuove configurazioni, sia inviate direttamente al nodo di destinazione o il rilevamento in un servizio di pull. Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log e quindi tenta di modificare la configurazione del nodo di destinazione per garantire la conformità con il file di configurazione.
- ConfigurationModeFrequencyMins Rappresenta la frequenza (in minuti) in corrispondenza del quale l'applicazione in background di DSC prova a implementare la configurazione corrente nel nodo di destinazione. Il valore predefinito è 15. Questo valore può essere impostato insieme a RefreshMode. Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il servizio di configurazione in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente. Indipendentemente dal valore di RefreshMode, il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins. La proprietà RefreshFrequencyMins deve essere impostata su un numero intero multiplo di ConfigurationModeFrequencyMins.
- -Credential Indica le credenziali (come con Get-Credential) necessarie per accedere alle risorse remote, ad esempio per contattare il servizio di configurazione.
- **DownloadManagerCustomData**: Rappresenta una matrice che contiene dati personalizzati specifici del gestore di download.
- **DownloadManagerName**: Indica il nome della configurazione e gestione di download di moduli.
- RebootNodeIfNeeded Alcune modifiche di configurazione in un nodo di destinazione potrebbero richiedere il riavvio applicare le modifiche. Con il valore **True**, questa proprietà riavvia il nodo non appena la configurazione viene applicata completamente, senza altri avvisi. Se **False** (valore predefinito), la configurazione viene completata, ma il nodo deve essere riavviato manualmente perché le modifiche abbiano effetto.
- RefreshFrequencyMins Utilizzato quando è stato configurato un servizio di pull. Rappresenta la frequenza (in minuti) in base alla quale Gestione configurazione locale contatta un servizio di pull per scaricare la configurazione corrente. Questo valore può essere impostato insieme a ConfigurationModeFrequencyMins. Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il servizio di pull in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente. Il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins. Se la proprietà RefreshFrequencyMins non è impostata su un numero intero multiplo di ConfigurationModeFrequencyMins, il sistema arrotonda questo valore. Il valore predefinito è 30.
- RefreshMode I valori possibili sono **Push** (predefinito) e **Pull**. Nella configurazione "push" è necessario inserire un file di configurazione in ogni nodo di destinazione, usando qualsiasi computer client. In modalità "pull" è necessario configurare un servizio di pull perché Gestione configurazione locale possa contattare i file di configurazione e accedervi.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Esempio di aggiornamento delle impostazioni di Gestione configurazione locale

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
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
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

L'esecuzione dello script dell'esempio precedente genera un file MOF che specifica e archivia le impostazioni desiderate.
Per applicare le impostazioni, è possibile usare il cmdlet **Set-DscLocalConfigurationManager**, come mostrato nell'esempio seguente.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Nota**: per il parametro **Path**, è necessario specificare lo stesso percorso specificato per il parametro **OutputPath** quando è stata richiamata la configurazione nell'esempio precedente.

Per visualizzare le impostazioni di Gestione configurazione locale correnti, è possibile usare il cmdlet **Get-DscLocalConfigurationManager**.
Se richiamato senza parametri, per impostazione predefinita questo cmdlet ottiene le impostazioni di Gestione configurazione locale per il nodo in cui viene eseguito.
Per specificare un altro nodo, usare il parametro **CimSession** con questo cmdlet.
