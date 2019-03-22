---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Registrazione delle configurazioni JEA
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059440"
---
# <a name="registering-jea-configurations"></a>Registrazione delle configurazioni JEA

> Si applica a: Windows PowerShell 5.0

Dopo aver creato le [funzionalità del ruolo](role-capabilities.md) e i [file di configurazione sessione](session-configurations.md), l'ultimo passaggio prima di poter usare JEA consiste nel registrare l'endpoint JEA.
La registrazione dell'endpoint JEA nel sistema rende l'endpoint disponibile per l'uso da parte degli utenti e dei motori di automazione.

## <a name="single-machine-configuration"></a>Configurazione di un computer singolo

Per gli ambienti di piccole dimensioni, è possibile distribuire JEA registrando il file di configurazione sessione tramite il cmdlet [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).

Prima di iniziare, verificare che siano soddisfatti i prerequisiti seguenti:
- Sono stati creati uno o più ruoli e inseriti nella cartella "RoleCapabilities" di un modulo di PowerShell valido.
- È stato creato e verificato un file di configurazione sessione.
- L'utente che registra la configurazione JEA ha diritti di amministratore sui sistemi.

È anche necessario selezionare un nome per l'endpoint JEA.
Il nome dell'endpoint JEA è necessario quando gli utenti vogliono connettersi al sistema tramite JEA.
È possibile usare il cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) per verificare i nomi degli endpoint esistenti nel sistema.
Gli endpoint che iniziano con "microsoft" sono in genere inclusi in Windows.
L'endpoint "microsoft.powershell" è l'endpoint predefinito usato per la connessione a un endpoint di PowerShell remoto.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Dopo aver definito un nome appropriato per l'endpoint JEA, eseguire il comando seguente per registrare l'endpoint.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Il comando riportato di sopra riavvia il servizio WinRM nel sistema.
> Questo comando termina tutte le sessioni di comunicazione remota di PowerShell e anche eventuali configurazioni DSC in corso.
> Per evitare di interrompere operazioni aziendali in corso, è consigliabile che ogni computer di produzione sia offline prima di eseguire il comando.

Se la registrazione ha esito positivo, è possibile [usare JEA](using-jea.md).
È possibile eliminare il file di configurazione sessione in qualsiasi momento perché non viene più usato dopo la registrazione dell'endpoint.

## <a name="multi-machine-configuration-with-dsc"></a>Configurazione di più computer con DSC

Se si distribuisce JEA su più computer, il modello di distribuzione più semplice consiste nell'usare la risorsa [Desired State Configuration (DSC)](https://msdn.microsoft.com/powershell/dsc/overview) di JEA per distribuire rapidamente e in modo coerente JEA in ogni computer.

Per distribuire JEA con DSC, è necessario assicurarsi che siano soddisfatti i prerequisiti seguenti:
- Sono state create una o più funzionalità del ruolo e aggiunte a un modulo di PowerShell valido.
- Il modulo di PowerShell che contiene i ruoli è archiviato in una condivisione di file (sola lettura) accessibile da ogni computer.
- Le impostazioni per la configurazione sessione sono state determinate. Non è necessario creare un file di configurazione sessione quando si usa la risorsa DSC di JEA.
- Sono disponibili le credenziali che consentono di eseguire azioni amministrative in ogni computer o di avere accesso a un server di pull DSC usato per gestire i computer.
- È stata scaricata la [risorse DSC di JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

In un computer di destinazione (o in un server di pull, se usato), creare una configurazione DSC per l'endpoint JEA.
In questa configurazione, si usa la risorsa DSC di Just Enough Administration (JEA) per impostare il file di configurazione sessione e la risorsa File per copiare le funzionalità di ruolo dalla condivisione file.

Le proprietà seguenti possono essere configurate tramite la risorsa DSC:
- Definizioni dei ruoli
- Gruppi di account virtuali
- Nome account del servizio gestito del gruppo
- Directory delle trascrizioni
- Unità utente
- Regole di accesso condizionale
- Script di avvio per la sessione JEA

La sintassi per ognuna di queste proprietà in una configurazione DSC è coerente con il file di configurazione sessione di PowerShell.

Di seguito è riportato un esempio di configurazione DSC per un modulo di manutenzione generale del server.

Si presuppone che un modulo valido di PowerShell che contiene le funzionalità del ruolo in una sottocartella "RoleCapabilities" si trovi nella condivisione file "\\\\myfileshare\\JEA".


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

Questa configurazione può quindi essere applicata in un sistema [chiamando direttamente Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig) o aggiornando la [configurazione server di pull](https://msdn.microsoft.com/powershell/dsc/pullserver).

La risorsa DSC consente anche di sostituire l'endpoint di comunicazione remota Microsoft.PowerShell predefinito.
In questo caso, la risorsa registra automaticamente un endpoint di backup senza vincoli denominato "Microsoft.PowerShell.Restricted" con il valore predefinito WinRM ACL, consentendo così ai membri del gruppo Utenti gestione remota e Administrators locale di accedere all'endpoint.

## <a name="unregistering-jea-configurations"></a>Annullamento delle configurazioni JEA

Per rimuovere un endpoint JEA da un sistema, usare il cmdlet [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).
L'annullamento della registrazione di un endpoint JEA impedisce ai nuovi utenti di creare sessioni JEA nuove nel sistema.
Ciò consente anche di aggiornare una configurazione JEA registrando di nuovo un file di configurazione sessione aggiornato con lo stesso nome di endpoint.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> L'annullamento della registrazione di un endpoint JEA causa il riavvio del servizio WinRM.
> Questa operazione interrompe la maggior parte delle operazioni di gestione remota in corso, incluse altre sessioni di PowerShell, le chiamate WMI e alcuni strumenti di gestione.
> Annullare solo la registrazione degli endpoint di PowerShell nelle finestre di manutenzione pianificata.

## <a name="next-steps"></a>Passaggi successivi

- [Testare l'endpoint JEA](using-jea.md)
