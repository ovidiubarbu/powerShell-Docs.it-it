---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurazioni parziali di PowerShell DSC (Desired State Configuration)
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401555"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Configurazioni parziali di PowerShell DSC (Desired State Configuration)

Si applica a: Windows PowerShell 5.0 e versioni successive._

In PowerShell 5.0, DSC (Desired State Configuration) consente di distribuire le configurazioni in frammenti e da più origini. Gestione configurazione locale nel nodo di destinazione riunisce i frammenti prima di applicarli come singola configurazione. Questa funzionalità consente di condividere il controllo della configurazione tra team o singoli utenti. Ad esempio, se due o più team di sviluppatori collaborano a un servizio, ogni team potrebbe voler creare configurazioni per gestire la propria parte del servizio. È possibile effettuare il pull di ognuna di queste configurazioni da server di pull diversi e aggiungere le configurazioni in fasi diverse del processo di sviluppo. Le configurazioni parziali consentono inoltre a persone o team diversi di controllare aspetti diversi della configurazione dei nodi senza la necessità di coordinare le modifiche di un singolo documento di configurazione. Un team, ad esempio, potrebbe essere responsabile della distribuzione di una VM e un sistema operativo, mentre un altro team potrebbe distribuire altri servizi e applicazioni in tale VM. Con le configurazioni parziali, ogni team può creare la sua configurazione, senza che alcuna di esse sia inutilmente complessa.

È possibile usare le configurazioni parziali in modalità push o pull o in una combinazione delle due modalità.

## <a name="partial-configurations-in-push-mode"></a>Configurazioni parziali in modalità push

Per usare le configurazioni parziali in modalità push, è necessario configurare Gestione configurazione locale nel nodo di destinazione per ricevere le configurazioni parziali. Il push di ogni configurazione parziale nella destinazione viene effettuato usando il cmdlet `Publish-DSCConfiguration`. Il nodo di destinazione combina quindi la configurazione parziale in una singola configurazione, che è possibile applicare chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Configurazione di Gestione configurazione locale per le configurazioni parziali in modalità push

Per configurare Gestione configurazione locale per le configurazioni parziali in modalità push, è necessario creare una configurazione **DSCLocalConfigurationManager** con un blocco **PartialConfiguration** per ogni configurazione parziale. Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](/powershell/dsc/metaConfig). L'esempio seguente illustra una configurazione di Gestione configurazione locale che prevede due configurazioni parziali, una che distribuisce il sistema operativo e una che distribuisce e configura SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

Il valore di **RefreshMode** per ogni configurazione parziale è "Push". I nomi dei blocchi **PartialConfiguration** (in questo caso, "ServiceAccountConfig" e "SharePointConfig") devono corrispondere esattamente ai nomi delle configurazioni di cui viene effettuato il push nel nodo di destinazione.

> [!Note]
> Il nome di ogni blocco **PartialConfiguration** deve corrispondere al nome effettivo della configurazione, come specificato nello script di configurazione, non al nome del file MOF, che deve essere il nome del nodo di destinazione o `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Pubblicazione e avvio di configurazioni parziali in modalità push

Chiamare quindi [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) per ogni configurazione, passando le cartelle che contengono i documenti di configurazione come parametri **Path**. `Publish-DSCConfiguration`inserisce i file MOF di configurazione nei nodi di destinazione. Dopo la pubblicazione di entrambe le configurazioni, è possibile chiamare `Start-DSCConfiguration –UseExisting` nel nodo di destinazione.

Ad esempio, se sono stati compilati i documenti MOF di configurazione seguenti nel nodo di creazione:

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

Le configurazioni verrebbero pubblicate ed eseguite come indicato di seguito:

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> L'utente che esegue il cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) deve avere privilegi di amministratore nel nodo di destinazione.

## <a name="partial-configurations-in-pull-mode"></a>Configurazioni parziali in modalità pull

È possibile effettuare il pull delle configurazioni parziali da uno o più server di pull. Per altre informazioni sui server di pull, vedere [Server di pull Windows PowerShell DSC (Desired Configuration Pull)](pullServer.md). A tale scopo, è necessario configurare Gestione configurazione locale nel nodo di destinazione per effettuare il pull delle configurazioni parziali, nonché assegnare un nome ai documenti di configurazione e posizionarli in modo appropriato nei server di pull.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Configurazione di Gestione configurazione locale per le configurazioni dei nodi di pull

Per configurare Gestione configurazione locale per il pull di configurazioni parziali da un server di pull, è necessario definire il server di pull in un blocco **ConfigurationRepositoryWeb** (per un server di pull HTTP) o **ConfigurationRepositoryShare** (per un server di pull SMB). Creare quindi blocchi **PartialConfiguration** che fanno riferimento al server di pull usando la proprietà **ConfigurationSource**. È anche necessario creare un blocco **Settings** per specificare che Gestione configurazione locale usa la modalità pull, nonché specificare il valore di **ConfigurationNames** o **ConfigurationID** usato dal server di pull e dal nodo di destinazione per identificare le configurazioni. La metaconfigurazione seguente definisce un server di pull HTTP denominato CONTOSO-PullSrv e due configurazioni parziali che usano tale server di pull.

Per informazioni sulla configurazione di Gestione configurazione locale tramite **ConfigurationNames**, vedere [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md). Per informazioni sulla configurazione di Gestione configurazione locale tramite **ConfigurationID**, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Configurazione di Gestione configurazione locale per configurazioni di modalità pull tramite nomi di configurazione

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Configurazione di Gestione configurazione locale per configurazioni di modalità pull tramite ID configurazione

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

È possibile effettuare il pull delle configurazioni parziali da più di un server di pull. A tale scopo, è sufficiente definire ogni server di pull e quindi fare riferimento al server di pull appropriato in ogni blocco **PartialConfiguration**.

Dopo aver creato la metaconfigurazione, è necessario eseguirla per creare un documento di configurazione (un file MOF) e quindi chiamare [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) per configurare Gestione configurazione locale.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Denominazione e posizionamento dei documenti di configurazione nel server di pull (ConfigurationNames)

I documenti di configurazione parziale devono essere inseriti nella cartella specificata come **ConfigurationPath** nel file `web.config` per il server di pull (in genere `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Assegnazione dei nomi ai documenti di configurazione nel server di pull in PowerShell 5.1

Se si esegue il pull solo di una configurazione parziale da un singolo server di pull, il documento di configurazione può avere qualsiasi nome. Se si esegue il pull di più di una configurazione parziale da un server di pull, il nome del documento di configurazione può essere `<ConfigurationName>.mof`, dove *ConfigurationName* è il nome della configurazione parziale, oppure `<ConfigurationName>.<NodeName>.mof`, dove *ConfigurationName* è il nome della configurazione parziale e *NodeName* è il nome del nodo di destinazione. Questo consente di eseguire il pull delle configurazioni dal server di pull DSC di Automazione di Azure.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Assegnazione dei nomi ai documenti di configurazione nel server di pull in PowerShell 5.0

I documenti di configurazione devono essere denominati come segue: `ConfigurationName.mof`, dove *ConfigurationName* è il nome della configurazione parziale. In questo esempio i nomi dei documenti di configurazione devono essere quelli indicati di seguito:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Denominazione e posizionamento dei documenti di configurazione nel server di pull (ConfigurationID)

I documenti di configurazione parziale devono essere inseriti nella cartella specificata come **ConfigurationPath** nel file `web.config` per il server di pull (in genere `C:\Program Files\WindowsPowerShell\DscService\Configuration`). I documenti di configurazione devono essere denominati come segue: `<ConfigurationName>.<ConfigurationID>.mof`, dove _ConfigurationName_ è il nome della configurazione parziale e _ConfigurationID_ è l'ID della configurazione definita in Gestione configurazione locale nel nodo di destinazione. In questo esempio i nomi dei documenti di configurazione devono essere quelli indicati di seguito:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Esecuzione di configurazioni parziali da un server di pull

Dopo aver configurato Gestione configurazione locale nel nodo di destinazione e dopo aver creato i documenti di configurazione e aver assegnato loro i nomi appropriati nel server di pull, il nodo di destinazione effettuerà il pull delle configurazioni parziali, le combinerà e applicherà la configurazione risultante a intervalli regolari, come specificato dalla proprietà **RefreshFrequencyMins** di Gestione configurazione locale. Se si vuole forzare un aggiornamento, è possibile chiamare il cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) per effettuare il pull delle configurazioni e quindi `Start-DSCConfiguration –UseExisting` per applicare le configurazioni.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Configurazioni parziali in modalità mista push e pull

È anche possibile combinare le modalità push e pull per le configurazioni parziali. In altre parole, è possibile usare una configurazione parziale di cui viene effettuato il pull da un server di pull e un'altra configurazione parziale di cui viene effettuato il push. Specificare la modalità di aggiornamento per ogni configurazione parziale, come descritto nelle sezioni precedenti. Ad esempio, la metaconfigurazione seguente descrive lo stesso esempio, con la configurazione parziale `ServiceAccountConfig` in modalità pull e la configurazione parziale `SharePointConfig` in modalità push.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Modalità miste push e pull che usano ConfigurationNames

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Modalità miste push e pull che usano ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Si noti che il valore di **RefreshMode** specificato nel blocco Settings è "Pull", mentre il valore di **RefreshMode** per la configurazione parziale `SharePointConfig` è "Push".

Denominare e posizionare i file MOF di configurazione come descritto in precedenza per le relative modalità di aggiornamento.
Chiamare `Publish-DSCConfiguration` per pubblicare la configurazione parziale `SharePointConfig` e attendere il pull della configurazione `ServiceAccountConfig` dal server di pull oppure forzare un aggiornamento chiamando [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Esempio di configurazione parziale di ServiceAccountConfig

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>Esempio di configurazione parziale di SharePointConfig

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Vedere anche

[Server di pull Windows PowerShell DSC (Desired Configuration Pull)](pullServer.md)

[Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)