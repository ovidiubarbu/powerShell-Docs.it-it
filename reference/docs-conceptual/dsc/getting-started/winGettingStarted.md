---
ms.date: 08/15/2019
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a DSC (Desired State Configuration) per Windows
ms.openlocfilehash: 2add2c936e60c0c9446bf4b398fbf7b4bd6407f7
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75416172"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Introduzione a DSC (Desired State Configuration) per Windows

Questo argomento illustra come iniziare a usare PowerShell DSC (Desired State Configuration) per Windows.
Per informazioni generali su DSC, vedere [Introduzione a Windows PowerShell DSC (Desired State Configuration)](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Versioni del sistema operativo Windows supportate

Sono supportate le versioni seguenti:

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

La SKU del prodotto autonomo [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) non contiene un'implementazione di DSC, di conseguenza non può essere gestito da PowerShell DSC o da State Configuration di Automazione di Azure.

## <a name="installing-dsc"></a>Installazione di DSC

PowerShell DSC è incluso in Windows e viene aggiornato tramite Windows Management Framework. La versione più recente è [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> Non è necessario abilitare la funzionalità "DSC-Service" di Windows Server per gestire un computer con DSC.
> Questa funzionalità è necessaria solo quando si crea un'istanza del server di pull Windows.

## <a name="using-dsc-for-windows"></a>Uso di DSC per Windows

Le sezioni seguenti illustrano come creare ed eseguire configurazioni DSC nei computer Windows.

### <a name="creating-a-configuration-mof-document"></a>Creazione di un documento MOF di configurazione

Per creare una configurazione, si usa la parola chiave `Configuration` di Windows PowerShell.
I passaggi seguenti descrivono la creazione di un documento di configurazione con Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Definire una configurazione e generare il documento di configurazione:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a>Installare un modulo contenente risorse DSC

Windows PowerShell DSC (Desired State Configuration) include moduli predefiniti contenenti le risorse DSC.
È anche possibile caricare moduli da origini esterne, ad esempio PowerShell Gallery, usando i cmdlet di PowerShellGet.

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a>Applicare la configurazione al computer

> [!NOTE]
> Per consentire l'esecuzione di DSC, è necessario configurare Windows per la ricezione di comandi remoti di PowerShell anche quando si esegue una configurazione `localhost`. Per configurare correttamente l'ambiente, è sufficiente eseguire `Set-WsManQuickConfig -Force` in un terminale di PowerShell con privilegi elevati.

È possibile applicare i documenti di configurazione (file MOF) al computer usando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a>Ottenere lo stato corrente della configurazione

Il cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) esegue una query per ottenere lo stato corrente del computer e restituisce i valori correnti per la configurazione.

```powershell
Get-DscConfiguration
```

Il cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) restituisce la metaconfigurazione corrente applicata al computer.

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a>Rimuovere la configurazione corrente da un computer

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a>Configurare le impostazioni in Gestione configurazione locale

Applicare un file MOF di metaconfigurazione al computer usando il cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).
Richiede il percorso del file MOF di metaconfigurazione.

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a>File di log di Windows PowerShell DSC (Desired State Configuration)

I log per DSC vengono scritti nel percorso `Microsoft-Windows-Dsc/Operational` di Registro eventi di Windows.
È possibile abilitare altri log a scopo di debug attenendosi alla procedura descritta in [Dove sono i registri eventi DSC?](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
