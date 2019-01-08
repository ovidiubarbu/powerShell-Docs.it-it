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
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="b2974-103">Aggiornare i nodi da un server di pull</span><span class="sxs-lookup"><span data-stu-id="b2974-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="b2974-104">Le sezioni seguenti presuppongono che già stato impostato in un Server di Pull.</span><span class="sxs-lookup"><span data-stu-id="b2974-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="b2974-105">Se non è stato configurato il Server di Pull, è possibile usare le guide seguenti:</span><span class="sxs-lookup"><span data-stu-id="b2974-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="b2974-106">Configurare un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="b2974-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b2974-107">Configurare un server di pull HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="b2974-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b2974-108">Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato.</span><span class="sxs-lookup"><span data-stu-id="b2974-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b2974-109">Questo articolo illustrerà come caricare risorse in modo che siano disponibili per essere scaricato e configurare i client per scaricare automaticamente le risorse.</span><span class="sxs-lookup"><span data-stu-id="b2974-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="b2974-110">Quando il nodo riceve una configurazione assegnata, attraverso **Pull** oppure **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="b2974-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="b2974-111">Usando il cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2974-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="b2974-112">A partire da PowerShell 5.0, il [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet forza un nodo per aggiornare la propria configurazione dal Server di Pull configurato in Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="b2974-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="b2974-113">Usando Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="b2974-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="b2974-114">In PowerShell 4.0, è possibile forzare manualmente un Client di Pull per aggiornare la configurazione usando [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="b2974-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="b2974-115">Nell'esempio seguente crea una sessione CIM con le credenziali specificate, richiama il metodo CIM appropriato e rimuove la sessione.</span><span class="sxs-lookup"><span data-stu-id="b2974-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="b2974-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b2974-116">See Also</span></span>

[<span data-ttu-id="b2974-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b2974-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
