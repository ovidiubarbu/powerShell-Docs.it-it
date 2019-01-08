---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, raccolta, il programma di installazione
title: Installare risorse DSC aggiuntive
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401693"
---
# <a name="install-additional-dsc-resources"></a>Installare risorse DSC aggiuntive

PowerShell include varie risorse di Out-of-the-box per Desired State Configuration (DSC). Il **PSDesiredStateConfiguration** modulo contiene tutte le risorse DSC OOB disponibili nell'istanza specifica di PowerShell.

Questo è un elenco delle risorse OOB incluse in PowerShell 4.0 e una descrizione delle funzionalità della risorsa.

> [!NOTE]
> Si tratta di un elenco incompleto, come il numero di risorse OOB è cresciuto con ogni versione di PowerShell.

|Resource  |Description  |
|---------|---------|
|**File**|Controlla lo stato di file e directory. Copia i file da un **origine** a un **destinazione** e li aggiorna quando il **origine** modifiche confrontando le date, i valori di checksum e hash.|
|**Archive**|È possibile decomprimere archivi e una posizione specificata. Convalida gli archivi con un oggetto specificato **Checksum**.|
|**Environment**|Gestisce le variabili di ambiente.|
|**Gruppo**|Gestisce i gruppi locali e controlla l'appartenenza al gruppo.|
|**Log**|Scrive i messaggi per il `Microsoft-Windows-Desired State Configuration/Analytic` registro eventi.|
|**Pacchetto**|Installa o disinstalla pacchetti usando **argomenti**, **LogPath**, **ReturnCode**, le altre impostazioni.|
|**Registry**|Gestisce i valori e le chiavi del Registro di sistema.|
|**Script**|Consente di progettare il proprio [get-test-set](../resources/get-test-set.md) blocchi di script.|
|**Service**|Configura i servizi di Windows.|
|**User** |Gestisce gli attributi e gli utenti locali.|
|**WindowsFeature**|Consente di gestire ruoli e funzionalità.|
|**WindowsProcess**|Configura i processi di Windows.|

Le risorse OOB consentono un buon punto di partenza per le operazioni comuni. Se le risorse OOB non soddisfano le proprie esigenze, è possibile scrivere il proprio [risorsa personalizzata](../resources/authoringResource.md). Prima di scrivere una risorsa personalizzata per risolvere i problemi, è necessario esaminare l'elevato numero di risorse DSC che sono già stati creati da Microsoft e la community di PowerShell.

È possibile trovare risorse DSC in entrambe le [PowerShell Gallery](https://www.powershellgallery.com/) e [GitHub](https://github.com/). È anche possibile installare le risorse DSC direttamente dalla console di PowerShell usando [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installazione di PowerShellGet

Per determinare se si ha già **PowerShell** ottenere o per ottenere assistenza installarlo, vedere la Guida seguente: [installazione PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Trovare risorse DSC con PowerShellGet

Una volta **PowerShellGet** sia installato nel sistema, è possibile trovare e installare le risorse DSC ospitate nel [PowerShell Gallery](https://www.powershellgallery.com/).

In primo luogo, usare il [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet per trovare le risorse DSC. Quando si esegue `Find-DSCResource` per la prima volta, viene visualizzata l'istruzione seguente per installare il provider"NuGet".

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Dopo aver premuto "y", viene installato il provider "NuGet", viene visualizzato un elenco di risorse DSC che possano installare da PowerShell Gallery.

> [!NOTE]
> Elenco non viene visualizzato perché è molto grande.

È inoltre possibile specificare il `-Name` utilizzano caratteri jolly, parametro o `-Filter` parametro senza caratteri jolly per restringere la ricerca. In questo esempio tenta di individuare una risorsa "Fuso orario" DSC usando i caratteri jolly.

> [!IMPORTANT]
> Attualmente c'è un bug nel `Find-DSCResource` cmdlet che impediscono di usare i caratteri jolly in entrambe le `-Name` e `-Filter` parametri. Il secondo esempio riportato di seguito illustra una soluzione alternativa usando `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

È anche possibile usare `Where-Object` per trovare le risorse DSC con un filtro più granulare. Questo approccio sarà più lento rispetto all'uso di parametri di filtro incorporata.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Per altre informazioni sui filtri, vedere [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installazione di risorse DSC con PowerShellGet

Per installare una risorsa DSC, usare il [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, che specifica il nome del modulo visualizzato sotto **modulo** nome nei risultati della ricerca.

La risorsa "Fuso orario" presente nel modulo "ComputerManagementDSC", in modo che sia che il modulo viene installato in questo esempio.

> [!NOTE]
> Se PowerShell gallery non è considerato attendibile, viene visualizzato l'avviso seguente in cui viene chiesto di confermare l'operazione e che indica come evitare le richieste successive su Installa.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Premere 'y' per continuare a installare il modulo. Dopo l'installazione, è possibile verificare che la nuova risorsa venga installata seguendo [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

È inoltre possibile visualizzare altre risorse nel modulo appena installato, specificando il `-ModuleName` parametro.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Vedere anche

- [Che cosa sono le risorse?](../resources/resources.md)
