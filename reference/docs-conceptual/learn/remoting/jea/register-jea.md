---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Registrazione delle configurazioni JEA
ms.openlocfilehash: dbed5c7dd71f2f7a09d97416be56dff675799548
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417605"
---
# <a name="registering-jea-configurations"></a>Registrazione delle configurazioni JEA

Dopo aver creato le [funzionalità del ruolo](role-capabilities.md) e i [file di configurazione della sessione](session-configurations.md), l'ultimo passaggio consiste nel registrare l'endpoint JEA. La registrazione dell'endpoint JEA nel sistema rende l'endpoint disponibile per l'uso da parte degli utenti e dei motori di automazione.

## <a name="single-machine-configuration"></a>Configurazione di un computer singolo

Per gli ambienti di piccole dimensioni, è possibile distribuire JEA registrando il file di configurazione sessione tramite il cmdlet [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).

Prima di iniziare, verificare che siano soddisfatti i prerequisiti seguenti:

- Sono stati creati uno o più ruoli e inseriti nella cartella **RoleCapabilities** di un modulo di PowerShell.
- È stato creato e verificato un file di configurazione sessione.
- L'utente che registra la configurazione JEA ha diritti di amministratore nel sistema.
- È stato selezionato un nome per l'endpoint JEA.

Il nome dell'endpoint JEA viene richiesto quando gli utenti si connettono al sistema tramite JEA. Il cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) visualizza un elenco dei nomi degli endpoint di un sistema. Gli endpoint che iniziano con `microsoft` sono in genere inclusi in Windows. L'endpoint `microsoft.powershell` è l'endpoint predefinito usato per la connessione a un endpoint di PowerShell remoto.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Eseguire il comando seguente per registrare l'endpoint.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Il comando precedente riavvia il servizio WinRM nel sistema. Questo comando termina tutte le sessioni di comunicazione remota di PowerShell ed eventuali configurazioni DSC in corso. Per evitare di interrompere le operazioni aziendali in corso, è consigliabile che i computer di produzione siano offline prima di eseguire il comando.

Dopo la registrazione, sarà possibile [usare JEA](using-jea.md). È possibile eliminare il file di configurazione della sessione in qualsiasi momento. Il file di configurazione non viene usato dopo la registrazione dell'endpoint.

## <a name="multi-machine-configuration-with-dsc"></a>Configurazione di più computer con DSC

Quando si distribuisce JEA su più computer, il modello di distribuzione più semplice consiste nell'usare la risorsa [Desired State Configuration (DSC)](/powershell/scripting/dsc/overview) di JEA per distribuire rapidamente e in modo coerente JEA in ogni computer.

Per distribuire JEA con DSC, assicurarsi che siano soddisfatti i prerequisiti seguenti:

- Sono state create una o più funzionalità del ruolo e aggiunte a un modulo di PowerShell.
- Il modulo di PowerShell che contiene i ruoli è archiviato in una condivisione di file (sola lettura) accessibile da ogni computer.
- Le impostazioni per la configurazione sessione sono state determinate. Non è necessario creare un file di configurazione della sessione quando si usa la risorsa DSC di JEA.
- Sono disponibili le credenziali che consentono di eseguire azioni amministrative in ogni computer o di accedere a un server di pull DSC usato per la gestione dei computer.
- È stata scaricata la [risorsa DSC di JEA](https://github.com/powershell/JEA/tree/master/DSC%20Resource).

Creare una configurazione DSC per l'endpoint JEA in un computer di destinazione o server di pull. In questa configurazione la risorsa DSC **JustEnoughAdministration** definisce il file di configurazione della sessione mentre la risorsa **File** copia le funzionalità di ruolo dalla condivisione file.

Le proprietà seguenti possono essere configurate tramite la risorsa DSC:

- Definizioni dei ruoli
- Gruppi di account virtuali
- Nome account del servizio gestito del gruppo
- Directory delle trascrizioni
- Unità utente
- Regole di accesso condizionale
- Script di avvio per la sessione JEA

La sintassi per ognuna di queste proprietà in una configurazione DSC è coerente con il file di configurazione sessione di PowerShell.

Di seguito è riportato un esempio di configurazione DSC per un modulo di manutenzione generale del server. Si presuppone che un modulo valido di PowerShell che contiene le funzionalità di ruolo sia disponibile nella condivisione file `\\myfileshare\JEA`.

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

La configurazione viene quindi applicata in un sistema chiamando direttamente [Gestione configurazione locale](/powershell/scripting/dsc/managing-nodes/metaConfig) o aggiornando la [configurazione del server di pull](/powershell/scripting/dsc/pull-server/pullServer).

La risorsa DSC consente anche di sostituire l'endpoint **Microsoft.PowerShell** predefinito. Quando viene eseguita la sostituzione, la risorsa registra automaticamente un endpoint di backup denominato **Microsoft.PowerShell.Restricted**. L'endpoint di backup ha un elenco di controllo di accesso WinRM predefinito che offre l'accesso agli utenti di gestione remota e ai membri del gruppo Amministratori locali.

## <a name="unregistering-jea-configurations"></a>Annullamento delle configurazioni JEA

Il cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) rimuove un endpoint JEA. L'annullamento della registrazione di un endpoint JEA impedisce ai nuovi utenti di creare sessioni JEA nuove nel sistema. Ciò consente anche di aggiornare una configurazione JEA registrando di nuovo un file di configurazione sessione aggiornato con lo stesso nome di endpoint.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> L'annullamento della registrazione di un endpoint JEA causa il riavvio del servizio WinRM. Questa operazione interrompe la maggior parte delle operazioni di gestione remota in corso, incluse altre sessioni di PowerShell, le chiamate WMI e alcuni strumenti di gestione. Annullare solo la registrazione degli endpoint di PowerShell nelle finestre di manutenzione pianificata.

## <a name="next-steps"></a>Passaggi successivi

[Testare l'endpoint JEA](using-jea.md)
