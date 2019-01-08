---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Aggiornare i nodi da un server di pull
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401128"
---
# <a name="update-nodes-from-a-pull-server"></a>Aggiornare i nodi da un server di pull

Le sezioni seguenti presuppongono che già stato impostato in un Server di Pull. Se non è stato configurato il Server di Pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato. Questo articolo illustrerà come caricare risorse in modo che siano disponibili per essere scaricato e configurare i client per scaricare automaticamente le risorse. Quando il nodo riceve una configurazione assegnata, attraverso **Pull** oppure **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Usando il cmdlet Update-DSCConfiguration

A partire da PowerShell 5.0, il [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet forza un nodo per aggiornare la propria configurazione dal Server di Pull configurato in Gestione configurazione locale.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Usando Invoke-CIMMethod

In PowerShell 4.0, è possibile forzare manualmente un Client di Pull per aggiornare la configurazione usando [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). Nell'esempio seguente crea una sessione CIM con le credenziali specificate, richiama il metodo CIM appropriato e rimuove la sessione.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Vedere anche

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
