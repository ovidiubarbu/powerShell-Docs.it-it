---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Aggiornare i nodi da un server di pull
ms.openlocfilehash: fa59a2f6574db2dbc96621be4326f1d5a55e5de9
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500666"
---
# <a name="update-nodes-from-a-pull-server"></a>Aggiornare i nodi da un server di pull

Le sezioni seguenti presuppongono che sia già stato configurato un server di pull. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato. Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e come configurare i client per scaricare automaticamente le risorse. Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Uso del cmdlet Update-DSCConfiguration

A partire da PowerShell 5.0, il cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) forza l'aggiornamento della configurazione di un nodo dal server di pull configurato in Gestione configurazione locale.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Uso di Invoke-CIMMethod

In PowerShell 4.0 è ancora possibile forzare manualmente l'aggiornamento della configurazione di un client di pull tramite [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). L'esempio seguente crea una sessione CIM con le credenziali specificate, richiama il metodo CIM appropriato e rimuove la sessione.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Vedere anche

[PerformRequiredConfigurationChecks](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
