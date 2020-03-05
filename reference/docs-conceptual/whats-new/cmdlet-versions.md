---
ms.date: 02/03/2020
keywords: powershell,core
title: Cronologia delle versioni di moduli e cmdlet
ms.openlocfilehash: e0fe9b263bdd0a5e1bedd0762b7613a4bbe02a58
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706130"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Cronologia delle versioni di moduli e cmdlet

Questo articolo elenca i moduli e i cmdlet inclusi nelle diverse versioni di PowerShell. Si tratta di un riepilogo delle informazioni disponibili nelle note sulla versione. Altre informazioni sono disponibili nelle note di rilascio:

- [Novità di PowerShell Core 6.2](what-s-new-in-powershell-core-62.md)
- [Novità di PowerShell Core 6.1](what-s-new-in-powershell-core-61.md)
- [Novità di PowerShell Core 6.0](what-s-new-in-powershell-core-60.md)
- [Modifiche di rilievo in PowerShell Core 6.0](breaking-changes-ps6.md)
- [Problemi noti in PowerShell Core 6.0](known-issues-ps6.md)

Queste informazioni sono in fase di aggiornamento. Si richiede di contribuire a mantenere aggiornate le informazioni.

## <a name="module-release-history"></a>Cronologia delle versioni dei moduli

|         Nome modulo/Versione PS          |   5.1   |   6.x   |   7.0   |   7.1   |     Note     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Solo Windows |
| ISE (introdotto nella versione 2.0)                   | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Solo Windows |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | Solo Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WsMan.Management                | &check; | &check; | &check; | &check; | Solo Windows |
| Modulo PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Solo Windows |
| PSReadline 1.x                            | &check; |         |         |         | Solo Windows |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Solo Windows |
| PSWorkflow                                | &check; |         |         |         | Solo Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Solo Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | Può essere installato in PowerShell 5.1 |

## <a name="cmdlet-release-history"></a>Cronologia delle versioni dei cmdlet

### <a name="cimcmdlets"></a>CimCmdlets

|         Nome del cmdlet         |   5.1   |   6.x   |   7.0   |   7.1   |     Note     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Solo Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Solo Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Solo Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Solo Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Solo Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Solo Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Solo Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Solo Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Solo Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Solo Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Solo Windows |

### <a name="ise-introduced-in-20"></a>ISE (introdotto nella versione 2.0)

|    Nome del cmdlet    |   5.1   | 6.x  |  7.0  |  7.1  |     Note     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Solo Windows |
| Import-IseSnippet | &check; |      |       |       | Solo Windows |
| New-IseSnippet    | &check; |      |       |       | Solo Windows |


### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Nome del cmdlet    |   5.1   |   6.x   |   7.0   |   7.1   | Note |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Nome del cmdlet            |   5.1   |   6.x   |   7.0   |   7.1   |            Note            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Solo Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Solo Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Solo Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Solo Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Solo Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Solo Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Solo Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Aggiunto il supporto Linux nella versione 6.2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | Aggiunto il supporto Linux nella versione 6.2 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Solo Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Aggiunto il supporto Linux nella versione 6.2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Solo Windows               |
| Get-Verb                          | &check; |         |         |         | Spostato in Microsoft.PowerShell.Utility 6.0 e versioni successive |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Solo Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Solo Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Solo Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Solo Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Solo Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Solo Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Solo Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Solo Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Nome del cmdlet   |   5.1   |   6.x   |   7.0   |   7.1   |     Note     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Solo Windows |
| Get-Counter    | &check; |         | &check; | &check; | Solo Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Solo Windows |
| Import-Counter | &check; |         |         |         | Solo Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | Solo Windows |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Nome del cmdlet    |   5.1   |   6.x   |   7.0   |   7.1   | Note |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Nome del cmdlet       |   5.1   | 6.x  |  7.0  |  7.1  |     Note     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Solo Windows |
| Disable-LocalUser       | &check; |      |       |       | Solo Windows |
| Enable-LocalUser        | &check; |      |       |       | Solo Windows |
| Get-LocalGroup          | &check; |      |       |       | Solo Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Solo Windows |
| Get-LocalUser           | &check; |      |       |       | Solo Windows |
| New-LocalGroup          | &check; |      |       |       | Solo Windows |
| New-LocalUser           | &check; |      |       |       | Solo Windows |
| Remove-LocalGroup       | &check; |      |       |       | Solo Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Solo Windows |
| Remove-LocalUser        | &check; |      |       |       | Solo Windows |
| Rename-LocalGroup       | &check; |      |       |       | Solo Windows |
| Rename-LocalUser        | &check; |      |       |       | Solo Windows |
| Set-LocalGroup          | &check; |      |       |       | Solo Windows |
| Set-LocalUser           | &check; |      |       |       | Solo Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Nome del cmdlet          |   5.1   |   6.x   |   7.0   |   7.1   |               Note               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Solo Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Solo Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Solo Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Solo Windows                     |
| Complete-Transaction          | &check; |         |         |         | Solo Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Solo Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Solo Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | Non supportato in macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Solo Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Solo Windows                     |
| Get-EventLog                  | &check; |         |         |         | Solo Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Solo Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Solo Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | Solo Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Solo Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Solo Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Solo Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Solo Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Solo Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Solo Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Solo Windows                     |
| Remove-Computer               | &check; |         |         |         | Solo Windows                     |
| Remove-EventLog               | &check; |         |         |         | Solo Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Solo Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Solo Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; |                                  |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Solo Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Solo Windows                     |
| Restore-Computer              | &check; |         |         |         | Solo Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Solo Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Solo Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Solo Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Solo Windows                     |
| Show-EventLog                 | &check; |         |         |         | Solo Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Solo Windows                     |
| Start-Transaction             | &check; |         |         |         | Solo Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | Aggiunto il supporto Linux/macOS nella versione 7.0 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Solo Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Solo Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Solo Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Solo Windows                     |
| Use-Transaction               | &check; |         |         |         | Solo Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | Non funziona in Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Solo Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Nome del cmdlet        |   5.1   | 6.x  |  7.0  |  7.1  |     Note     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Solo Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Nome del cmdlet         |   5.1   | 6.x  |  7.0  |  7.1  |     Note     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Solo Windows |
| Invoke-OperationValidation | &check; |      |       |       | Solo Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Nome del cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   |                  Note                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Solo Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Solo Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Solo Windows                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Restituisce **Senza restrizioni** in Linux/macOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Solo Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Solo Windows                            |
| Set-Acl                   | &check; | &check; | &check; | &check; | Solo Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Solo Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Non esegue alcuna operazione in Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Solo Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Solo Windows                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Nome del cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   |                   Note                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Non sono disponibili origini evento in Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; |                                           |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Non sono disponibili origini evento in Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; |                                           |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Non sono disponibili origini evento in Linux/macOS |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Non sono disponibili origini evento in Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; |                                           |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | Aggiunto il supporto per macOS nella versione 7.0            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Non sono disponibili origini evento in Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WsMan.Management

|      Nome del cmdlet       |   5.1   |   6.x   |   7.0   |   7.1   |     Note     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Solo Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Solo Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Solo Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Solo Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Solo Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Solo Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Solo Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Solo Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Solo Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Solo Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Solo Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | Solo Windows |

### <a name="packagemanagement"></a>Modulo PackageManagement

|       Nome del cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   | Note |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Nome del cmdlet           |   5.1   |   6.x   |   7.0   |   7.1   | Note |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Nome del cmdlet                 |   5.1   |   6.x   |   7.0   |   7.1   |     Note     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Solo Windows |
| Enable-DscDebug                            | &check; |         |         |         | Solo Windows |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Solo Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Solo Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Solo Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialize-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Solo Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Solo Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Solo Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Solo Windows |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Solo Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Solo Windows |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Solo Windows |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | Solo Windows |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Write-Log                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Nome del cmdlet          |   5.1   |   6.x   |   7.0   |   7.1   |     Note     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Solo Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Solo Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Solo Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Solo Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Solo Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Solo Windows |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | Solo Windows |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | Solo Windows |

### <a name="psreadline"></a>PSReadline

|         Nome del cmdlet         |   5.1   |   6.x   |   7.0   |   7.1   | Note |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Nome del cmdlet       |   5.1   | 6.x  |  7.0  |  7.1  |     Note     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Solo Windows |
| Disable-JobTrigger      | &check; |      |       |       | Solo Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Solo Windows |
| Enable-JobTrigger       | &check; |      |       |       | Solo Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Solo Windows |
| Get-JobTrigger          | &check; |      |       |       | Solo Windows |
| Get-ScheduledJob        | &check; |      |       |       | Solo Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Solo Windows |
| New-JobTrigger          | &check; |      |       |       | Solo Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Solo Windows |
| Register-ScheduledJob   | &check; |      |       |       | Solo Windows |
| Remove-JobTrigger       | &check; |      |       |       | Solo Windows |
| Set-JobTrigger          | &check; |      |       |       | Solo Windows |
| Set-ScheduledJob        | &check; |      |       |       | Solo Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Solo Windows |
| Unregister-ScheduledJob | &check; |      |       |       | Solo Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Nome del cmdlet          |   5.1   | 6.x  |  7.0  |  7.1  |     Note     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Solo Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Solo Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Solo Windows |

### <a name="threadjob"></a>ThreadJob

|   Nome del cmdlet   |  5.1  |   6.x   |   7.0   |   7.1   | Note |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | Può essere installato in PowerShell 5.1 |
