---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di Gestione configurazione locale nelle versioni precedenti di Windows PowerShell
ms.openlocfilehash: 945d2dc95304a347ec26f2f66f5a17bfefb90997
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683009"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Configurazione di Gestione configurazione locale nelle versioni precedenti di Windows PowerShell

>Si applica a: Windows PowerShell 4.0

**Per informazioni correlate a Windows PowerShell 5.0 e versioni successive, vedere [Configurazione di Gestione configurazione locale](metaConfig.md).**

Gestione configurazione locale è il motore di Windows PowerShell DSC (Desired State Configuration).
Viene eseguito in tutti i nodi di destinazione e ha la responsabilità di chiamare le risorse di configurazione incluse in uno script di configurazione DSC.
Questo argomento contiene l'elenco delle proprietà di Gestione configurazione locale e descrive in che modo modificare le impostazioni di Gestione configurazione locale in un nodo di destinazione.

## <a name="local-configuration-manager-properties"></a>Proprietà di Gestione configurazione locale

Di seguito sono elencate le proprietà di Gestione configurazione locale che è possibile impostare o recuperare.

- **AllowModuleOverwrite**: controlla se le nuove configurazioni scaricate dal servizio di configurazione possono sovrascrivere quelle meno recenti nel nodo di destinazione. I possibili valori sono True e False.
- **CertificateID**: l'identificazione personale di un certificato usato per proteggere le credenziali passate in una configurazione. Per altre informazioni, vedere [Protezione delle credenziali in Windows PowerShell DSC (Desired State Configuration)](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID**: indica un GUID usato per ottenere un file di configurazione specifico da un servizio di pull. Il GUID garantisce l'accesso al file di configurazione corretto.
- **ConfigurationMode**: specifica il modo in cui Gestione configurazione locale applica effettivamente la configurazione ai nodi di destinazione. Può accettare i valori seguenti:
  - **ApplyOnly**: con questa opzione, DSC applica la configurazione e non esegue altre operazioni, a meno che non venga rilevata una nuova configurazione quando si invia una nuova configurazione direttamente al nodo di destinazione o se ci si connette a un servizio di pull e DSC individua una nuova configurazione quando controlla nel servizio di pull. Se la configurazione del nodo di destinazione non è sincronizzata, non viene eseguita alcuna azione.
  - **ApplyAndMonitor**: con questa opzione (che è quella predefinita), DSC applica tutte le nuove configurazioni, sia quelle inviate direttamente al nodo di destinazione sia quelle individuate in un servizio di pull. Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log. Per altre informazioni sulla registrazione di DSC, vedere la pagina sull'[uso di registri eventi per la diagnosi di errori in DSC (Desired State Configuration)](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: con questa opzione, DSC applica tutte le nuove configurazioni, sia quelle inviate direttamente al nodo di destinazione sia quelle individuate in un servizio di pull. Quindi, se la configurazione del nodo di destinazione non è sincronizzata rispetto al file di configurazione, DSC segnala la discrepanza nei log e quindi tenta di modificare la configurazione del nodo di destinazione per garantire la conformità con il file di configurazione.
- **ConfigurationModeFrequencyMins**: rappresenta la frequenza (in minuti) con la quale l'applicazione in background di DSC tenta di implementare la configurazione corrente nel nodo di destinazione. Il valore predefinito è 15. Questo valore può essere impostato insieme a RefreshMode. Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il servizio di configurazione in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente. Indipendentemente dal valore di RefreshMode, il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins. La proprietà RefreshFrequencyMins deve essere impostata su un numero intero multiplo di ConfigurationModeFrequencyMins.
- **Credential**: indica le credenziali (come con Get-Credential) necessarie per accedere alle risorse remote, ad esempio per contattare il servizio di configurazione.
- **DownloadManagerCustomData**: rappresenta una matrice che contiene dati personalizzati specifici del gestore di download.
- **DownloadManagerName**: indica il nome del gestore di download di configurazioni e moduli.
- **RebootNodeIfNeeded**: Impostare questa opzione su `$true` per consentire alle risorse riavviare il nodo mediante il `$global:DSCMachineStatus` flag. In caso contrario, sarà necessario riavviare manualmente il nodo per qualsiasi configurazione che lo richiede. Il valore predefinito è `$false`. Per usare questa impostazione quando una condizione di ravvio viene applicata da un componente diverso da DSC (ad esempio Windows Installer), combinare questa impostazione con il modulo [xPendingReboot](https://github.com/powershell/xpendingreboot).
- **RefreshFrequencyMins**: proprietà usata quando è stato configurato un servizio di pull. Rappresenta la frequenza (in minuti) in base alla quale Gestione configurazione locale contatta un servizio di pull per scaricare la configurazione corrente. Questo valore può essere impostato insieme a ConfigurationModeFrequencyMins. Quando la proprietà RefreshMode è impostata su PULL, il nodo di destinazione contatta il servizio di pull in base a un intervallo impostato tramite RefreshFrequencyMins e scarica la configurazione corrente. Il motore di coerenza applica la configurazione più recente scaricata al nodo di destinazione in base all'intervallo impostato tramite ConfigurationModeFrequencyMins. Se la proprietà RefreshFrequencyMins non è impostata su un numero intero multiplo di ConfigurationModeFrequencyMins, il sistema arrotonda questo valore. Il valore predefinito è 30.
- **RefreshMode**: i possibili valori sono **Push** (predefinito) e **Pull**. Nella configurazione "push" è necessario inserire un file di configurazione in ogni nodo di destinazione, usando qualsiasi computer client. In modalità "pull" è necessario configurare un servizio di pull perché Gestione configurazione locale possa contattare i file di configurazione e accedervi.

> [!NOTE]
> L'avvio di Gestione configurazione locale di **ConfigurationModeFrequencyMins** ciclo di base:
>
> - Viene applicata una metaconfig nuovo usando `Set-DscLocalConfigurationManager`
> - Riavvio del computer
>
> Per qualsiasi condizione in cui il processo timer si verifichi un arresto anomalo del sistema, che viene rilevato entro 30 secondi e il ciclo verrà riavviato.
> Un'operazione simultanea potrebbe ritardare il ciclo di avvio, se la durata dell'operazione supera la frequenza dei cicli configurato, il prossimo timer non verrà avviato.
>
> La metaconfigurazione di esempio è configurato con una frequenza di pull di 15 minuti e si verifica un'operazione pull all'ora T1.  Il nodo non viene completata lavoro per 16 minuti.  Il primo ciclo di 15 minuti viene ignorato e pull successivo avverrà alle T1 + 15 + 15.

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
