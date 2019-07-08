---
ms.date: 12/12/2018
keywords: dsc,powershell,risorsa,raccolta,configurazione
title: Installare risorse DSC aggiuntive
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080082"
---
# <a name="install-additional-dsc-resources"></a>Installare risorse DSC aggiuntive

PowerShell include varie risorse predefinite per Desired State Configuration (DSC). Il modulo **PSDesiredStateConfiguration** contiene tutte le risorse DSC predefinite disponibili nell'istanza specifica di PowerShell.

Questo è un elenco delle risorse OOB incluse in PowerShell 4.0 e una descrizione delle funzionalità della risorsa.

> [!NOTE]
> Si tratta di un elenco incompleto, in quanto il numero di risorse OOB è aumentato con ogni versione di PowerShell.

|Resource  |Description  |
|---------|---------|
|**File**|Controlla lo stato dei file e delle directory. Copia i file da un'**origine** a una **destinazione** e li aggiorna quando l'**origine** viene modificata confrontando le date, i valori di checksum e gli hash.|
|**Archive**|Decomprime archivi e una posizione specificata. Convalida gli archivi con un oggetto **Checksum** specificato.|
|**Environment**|Gestisce le variabili di ambiente.|
|**Gruppo**|Gestisce i gruppi locali e controlla l'appartenenza al gruppo.|
|**Log**|Scrive i messaggi sul registro eventi `Microsoft-Windows-Desired State Configuration/Analytic`.|
|**Pacchetto**|Installa o disinstalla i pacchetti usando **Arguments**, **LogPath**, **ReturnCode** e altre impostazioni.|
|**Registry**|Gestisce i valori e le chiavi del Registro di sistema.|
|**Script**|Consente di progettare il propri blocchi di script [get-test-set](../resources/get-test-set.md).|
|**Service**|Configura i servizi di Windows.|
|**User** |Gestisce gli utenti e gli attributi locali.|
|**WindowsFeature**|Gestisce i ruoli e le funzionalità.|
|**WindowsProcess**|Configura i processi di Windows.|

Le risorse OOB sono un buon punto di partenza per le operazioni comuni. Se le risorse OOB non soddisfano le proprie esigenze, è possibile scrivere una propria [risorsa personalizzata](../resources/authoringResource.md). Prima di scrivere una risorsa personalizzata per risolvere i problemi, è necessario esaminare l'elevato numero di risorse DSC che sono già state create dalla community Microsoft e PowerShell.

È possibile trovare risorse DSC sia in [PowerShell Gallery](https://www.powershellgallery.com/) che in [GitHub](https://github.com/). È anche possibile installare le risorse DSC direttamente dalla console di PowerShell usando [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installazione di PowerShellGet

Per determinare se si ha già **PowerShellGet** o per ottenere assistenza nell'installazione, vedere la guida seguente: [Installazione di PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Trovare risorse DSC con PowerShellGet

Una volta eseguita l'installazione di **PowerShellGet** nel sistema, è possibile trovare e installare le risorse DSC ospitate in [PowerShell Gallery](https://www.powershellgallery.com/).

In primo luogo, usare il cmdlet [Find-DSCResource](/powershell/module/powershellget/find-dscresource) per trovare le risorse DSC. Quando si esegue `Find-DSCResource` per la prima volta, viene visualizzato il seguente messaggio per installare il "provider NuGet".

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

Dopo aver premuto "Y", viene installato il provider "NuGet" e viene visualizzato un elenco di risorse DSC che è possibile installare da PowerShell Gallery.

> [!NOTE]
> L'elenco non viene visualizzato perché è molto grande.

È inoltre possibile specificare il parametro `-Name` usando caratteri jolly o il parametro `-Filter` senza caratteri jolly per restringere la ricerca. Questo esempio tenta di individuare una risorsa DSC "TimeZone" usando i caratteri jolly.

> [!IMPORTANT]
> Attualmente nel cmdlet `Find-DSCResource` è presente un bug che impedisce di usare i caratteri jolly nei parametri `-Name` e `-Filter`. Il secondo esempio riportato di seguito illustra una soluzione alternativa usando `Where-Object`.

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

È anche possibile usare `Where-Object` per trovare le risorse DSC con un filtro più granulare. Questo approccio sarà più lento rispetto all'uso di parametri di filtro incorporati.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Per altre informazioni sui filtri, vedere [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installazione di risorse DSC con PowerShellGet

Per installare una risorsa DSC, usare il cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module), che specifica il nome del modulo visualizzato nel nome **Modulo** nei risultati della ricerca.

La risorsa "TimeZone" esiste nel modulo "ComputerManagementDSC", pertanto questo è il modulo installato in questo esempio.

> [!NOTE]
> Se PowerShell Gallery non è considerato attendibile, viene visualizzato l'avviso seguente in cui viene chiesto di confermare l'operazione e che indica come evitare le richieste successive durante le installazioni.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Premere 'y' per continuare l'installazione del modulo. Dopo l'installazione, è possibile verificare che la nuova risorsa sia installata mediante [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

È inoltre possibile visualizzare altre risorse nel modulo appena installato, specificando il parametro`-ModuleName`.

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
