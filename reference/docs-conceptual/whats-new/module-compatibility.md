---
title: Compatibilità dei moduli PowerShell 7
ms.date: 02/03/2020
ms.openlocfilehash: 02095b8233b6fc7b6d2a30bcb841bfd831a50031
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "78935184"
---
# <a name="powershell-7-module-compatibility"></a>Compatibilità dei moduli PowerShell 7

Questo articolo contiene un elenco di moduli PowerShell pubblicati da Microsoft. Questi moduli offrono gestione e supporto per vari prodotti e servizi Microsoft. Questi moduli sono stati aggiornati per funzionare in modo nativo con PowerShell 7 oppure testati per la compatibilità con PowerShell 7. Questo elenco verrà aggiornato con nuove informazioni quando verranno identificati e testati altri moduli.

Se si hanno informazioni da condividere o problemi relativi a moduli specifici, segnalarli nel [repository WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility).

## <a name="windows-management-modules"></a>Moduli di gestione Windows

I moduli di gestione Windows vengono installati in diversi modi a seconda dell'edizione di Windows e di come è stato creato il pacchetto del modulo per l'edizione.

In Windows Server usare il nome della funzionalità con il cmdlet [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) come amministratore. Ad esempio:

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

In Windows 10 i moduli di gestione Windows sono resi disponibili come **funzionalità facoltative di Windows** o **funzionalità di Windows**. Eseguire i comandi seguenti da una sessione con privilegi elevati usando **Esegui come amministratore**.


- Per le funzionalità facoltative di Windows

  Per ottenere un elenco di funzionalità facoltative, eseguire il comando seguente:

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  Per installare la funzionalità:

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  Per altre informazioni, vedere:

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- Per le funzionalità di Windows

  Per ottenere un elenco di funzionalità di Windows, eseguire il comando seguente:

  ```powershell
  Get-WindowsCapability -online
  ```

  Notare che il nome del pacchetto della funzionalità termina con `~~~~0.0.1.0`. Per installare la funzionalità è necessario usare il nome completo:

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  Per altre informazioni, vedere:

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>Elenco dei moduli

| Nome del modulo                        | Stato                               | Sistema operativo supportato                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| ActiveDirectory                    | Compatibile in modo nativo                  | Windows Server 1809+ con RSAT-AD-PowerShell<br>Windows 10 1809+ con Rsat.ActiveDirectory.DS-LDS.Tools |
| AD FS                               | Non testato con il livello di compatibilità    |                                    |
| AppBackgroundTask                  | Compatibile in modo nativo                  | Windows 10 1903+                   |
| AppLocker                          | Non testato con il livello di compatibilità    |                                    |
| AppvClient                         | Non testato con il livello di compatibilità    |                                    |
| Appx                               | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+ |
| AssignedAccess                     | Compatibile in modo nativo                  | Windows 10 1809+                   |
| BestPractices                      | Non testato con il livello di compatibilità    |                                    |
| BitLocker                          | Compatibile in modo nativo                  | Windows Server 1809+ con BitLocker<br>Windows 10 1809+ |
| BitsTransfer                       | Compatibile in modo nativo                  | Windows Server 20H1<br>Windows 10 20H1 |
| BootEventCollector                 | Non testato con il livello di compatibilità    |                                        |
| BranchCache                        | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+ |
| CimCmdlets                         | Compatibile in modo nativo                  | Integrato in PowerShell 7 |
| ClusterAwareUpdating               | Non testato con il livello di compatibilità    |                         |
| ConfigCI                           | Non testato con il livello di compatibilità    |                         |
| Defender                           | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+  |
| DeliveryOptimization               | Compatibile in modo nativo                  | Windows Server 1903+<br>Windows 10 1903+  |
| DFSN                               | Compatibile in modo nativo                  | Windows Server 1809+ con FS-DFS-Namespace<br>Windows 10 1809+ con Rsat.FailoverCluster.Management.Tools |
| DFSR                               | Non testato con il livello di compatibilità    |                                   |
| DhcpServer                         | Non testato con il livello di compatibilità    |                                   |
| DirectAccessClientComponents       | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+  |
| Dism                               | Compatibile in modo nativo                  | Windows Server 1903+<br>Windows 10 1903+  |
| DnsClient                          | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+  |
| DnsServer                          | Compatibile in modo nativo                  | Windows Server 1809+ con DNS o RSAT-DNS-Server<br>Windows 10 1809+ con Rsat.Dns.Tools |
| EventTracingManagement             | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+  |
| FailoverClusters                   | Non testato con il livello di compatibilità    |                                  |
| FailoverClusterSet                 | Non testato con il livello di compatibilità    |                                  |
| FileServerResourceManager          | Compatibile in modo nativo                  | Windows Server 1809+ con FS-Resource-Manager |
| GroupPolicy                        | Non testato con il livello di compatibilità    |                                               |
| HgsClient                          | Compatibile in modo nativo                  | Windows Server 1903+ con Hyper-V o RSAT-Shielded-VM-Tools<br>Windows 10 1903+ con Rsat.Shielded.VM.Tools |
| HgsDiagnostics                     | Compatibile in modo nativo                  | Windows Server 1809+ con Hyper-V o RSAT-Shielded-VM-Tools<br>Windows 10 1809+ con Rsat.Shielded.VM.Tools |
| Hyper-V                            | Compatibile in modo nativo                  | Windows Server 1809+ con Hyper-V-PowerShell<br>Windows 10 1809+ con Microsoft-Hyper-V-Management-PowerShell |
| IISAdministration                  | Non testato con il livello di compatibilità    |                                               |
| International                      | Compatibile in modo nativo                  | Windows Server 1903+<br>Windows 10 1903+      |
| IpamServer                         | Non testato con il livello di compatibilità    |                                               |
| iSCSI                              | Non testato con il livello di compatibilità    |                                               |
| IscsiTarget                        | Non testato con il livello di compatibilità    |                                               |
| ISE                                | Non testato con il livello di compatibilità    |                                               |
| Kds                                | Compatibile in modo nativo                  | Windows Server 20H1<br>Windows 10 20H1        |
| Microsoft.PowerShell.Archive       | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| Microsoft.PowerShell.Diagnostics   | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| Microsoft.PowerShell.Host          | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| Microsoft.PowerShell.LocalAccounts | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| Microsoft.PowerShell.Management    | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| Microsoft.PowerShell.ODataUtils    | Non testato con il livello di compatibilità    |                                               |
| Microsoft.PowerShell.Security      | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| Microsoft.PowerShell.Utility       | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| Microsoft.WSMan.Management         | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| MMAgent                            | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| MPIO                               | Compatibile in modo nativo                  | Windows Server 1809+ con Multipath-IO        |
| MsDtc                              | Non testato con il livello di compatibilità    |                                               |
| NetAdapter                         | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetConnection                      | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetEventPacketCapture              | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetLbfo                            | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetLldpAgent                       | Non testato con il livello di compatibilità    |                                               |
| NetNat                             | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetQos                             | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetSecurity                        | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetSwitchTeam                      | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetTCPIP                           | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetWNV                             | Non testato con il livello di compatibilità    |                                               |
| NetworkConnectivityStatus          | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetworkController                  | Non testato con il livello di compatibilità    |                                               |
| NetworkControllerDiagnostics       | Non testato con il livello di compatibilità    |                                               |
| NetworkLoadBalancingClusters       | Non testato con il livello di compatibilità    |                                               |
| NetworkSwitchManager               | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetworkTransition                  | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| NFS                                | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+ con Rsat.ServerManager.Tools |
| Modulo PackageManagement                  | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| PcsvDevice                         | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| PersistentMemory                   | Non testato con il livello di compatibilità    |                                               |
| PKI                                | Non testato con il livello di compatibilità    |                                               |
| PnpDevice                          | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| PowerShellGet                      | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| PrintManagement                    | Compatibile in modo nativo                  | Windows Server 1903+ con Print-Services<br>Windows 10 1903+  |
| ProcessMitigations                 | Compatibile in modo nativo                  | Windows Server 1903+<br>Windows 10 1903+      |
| Provisioning                       | Non testato con il livello di compatibilità    |                                               |
| PSDesiredStateConfiguration        | Parzialmente                            | Integrato in PowerShell 7                       |
| PSDiagnostics                      | Compatibile in modo nativo                  | Integrato in PowerShell 7                       |
| PSScheduledJob                     | Non funzionante con il livello di compatibilità | Integrato in PowerShell 5.1                     |
| PSWorkflow                         | Non testato con il livello di compatibilità    |                                               |
| PSWorkflowUtility                  | Non testato con il livello di compatibilità    |                                               |
| RemoteAccess                       | Non testato con il livello di compatibilità    |                                               |
| RemoteDesktop                      | Non testato con il livello di compatibilità    |                                               |
| ScheduledTasks                     | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| SecureBoot                         | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| ServerCore                         | Non testato con il livello di compatibilità    |                                               |
| ServerManager                      | Non testato con il livello di compatibilità    |                                               |
| ServerManagerTasks                 | Non testato con il livello di compatibilità    |                                               |
| ShieldedVMDataFile                 | Compatibile in modo nativo                  | Windows Server 1903+ con RSAT-Shielded-VM-Tools<br>Windows 10 1903+ con Rsat.Shielded.VM.Tools |
| ShieldedVMProvisioning             | Compatibile in modo nativo                  | Windows Server 1809+ con HostGuardian<br>Windows 10 1809+ con HostGuardian  |
| ShieldedVMTemplate                 | Compatibile in modo nativo                  | Windows Server 1809+ con RSAT-Shielded-VM-Tools<br>Windows 10 1809+ con Rsat.Shielded.VM.Tools |
| SmbShare                           | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| SmbWitness                         | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| SMISConfig                         | Compatibile in modo nativo                  | Windows Server 1903+ con WindowsStorageManagementService |
| sms                                | Non testato con il livello di compatibilità    |                                               |
| SoftwareInventoryLogging           | Compatibile in modo nativo                  | Windows Server 1809+                          |
| StartLayout                        | Compatibile in modo nativo                  | Windows Server 1809+ con Esperienza desktop<br>Windows 10 1809+ |
| Archiviazione                            | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| StorageBusCache                    | Non testato con il livello di compatibilità    |                                               |
| StorageMigrationService            | Non testato con il livello di compatibilità    |                                               |
| StorageQOS                         | Compatibile in modo nativo                  | Windows Server 1809+ con RSAT-Clustering-PowerShell<br>Windows 10 1809+ con Rsat.FailoverCluster.Management.Tools |
| StorageReplica                     | Non testato con il livello di compatibilità    |                                               |
| SyncShare                          | Compatibile in modo nativo                  | Windows Server 1809+ con FS-SyncShareService |
| SystemInsights                     | Non testato con il livello di compatibilità    |                                               |
| TLS                                | Non testato con il livello di compatibilità    |                                               |
| TroubleshootingPack                | Compatibile in modo nativo                  | Windows 10 1903+                              |
| TrustedPlatformModule              | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| UEV                                | Compatibile in modo nativo                  | Windows Server??Versione futura del server con Esperienza desktop??<br>Windows 10 1903+ |
| UpdateServices                     | Non funzionante con il livello di compatibilità |                                               |
| VpnClient                          | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| Wdac                               | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| WebAdministration                  | Non testato con il livello di compatibilità    |                                               |
| WHEA                               | Compatibile in modo nativo                  | Windows Server 1903+<br>Windows 10 1903+      |
| WindowsDeveloperLicense            | Compatibile in modo nativo                  | Windows Server 1809+ con Esperienza desktop<br>Windows 10 1809+ |
| WindowsErrorReporting              | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+      |
| WindowsSearch                      | Compatibile in modo nativo                  | Windows 10 1903+                              |
| WindowsServerBackup                | Compatibile in modo nativo                  | Windows Server 19H2 con Windows-Server-Backup |
| WindowsUpdate                      | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+       |
| WindowsUpdateProvider              | Compatibile in modo nativo                  | Windows Server 1809+<br>Windows 10 1809+       |
