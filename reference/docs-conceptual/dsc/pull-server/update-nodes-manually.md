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
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="64dc4-103">Aggiornare i nodi da un server di pull</span><span class="sxs-lookup"><span data-stu-id="64dc4-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="64dc4-104">Le sezioni seguenti presuppongono che sia già stato configurato un server di pull.</span><span class="sxs-lookup"><span data-stu-id="64dc4-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="64dc4-105">Per configurare un server di pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="64dc4-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="64dc4-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="64dc4-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="64dc4-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="64dc4-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="64dc4-108">Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="64dc4-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="64dc4-109">Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e come configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="64dc4-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="64dc4-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).</span><span class="sxs-lookup"><span data-stu-id="64dc4-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="64dc4-111">Uso del cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="64dc4-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="64dc4-112">A partire da PowerShell 5.0, il cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) forza l'aggiornamento della configurazione di un nodo dal server di pull configurato in Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="64dc4-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="64dc4-113">Uso di Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="64dc4-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="64dc4-114">In PowerShell 4.0 è ancora possibile forzare manualmente l'aggiornamento della configurazione di un client di pull tramite [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="64dc4-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="64dc4-115">L'esempio seguente crea una sessione CIM con le credenziali specificate, richiama il metodo CIM appropriato e rimuove la sessione.</span><span class="sxs-lookup"><span data-stu-id="64dc4-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="64dc4-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="64dc4-116">See Also</span></span>

[<span data-ttu-id="64dc4-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="64dc4-117">PerformRequiredConfigurationChecks</span></span>](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
