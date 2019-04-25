---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.topic: conceptual
contributor: vaibch
title: Errore dei cmdlet per la gestione dei commutatori di rete
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084981"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="a7724-103">Errore dei cmdlet per la gestione dei commutatori di rete</span><span class="sxs-lookup"><span data-stu-id="a7724-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="a7724-104">Questi cmdlet consentono di gestire i commutatori di rete su WS-Management.</span><span class="sxs-lookup"><span data-stu-id="a7724-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="a7724-105">Alcuni cmdlet di questo modulo sono in grado di accettare i valori dalle pipeline.</span><span class="sxs-lookup"><span data-stu-id="a7724-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="a7724-106">In WMF 5.1 (anteprima) i cmdlet di questo tipo non vengono eseguiti quando le pipeline non permettono il passaggio dei valori.</span><span class="sxs-lookup"><span data-stu-id="a7724-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="a7724-107">Se non viene usato il parametro "InputObject", l'esecuzione del cmdlet dovrebbe continuare senza errori.</span><span class="sxs-lookup"><span data-stu-id="a7724-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="a7724-108">Di seguito è riportato l'elenco dei cmdlet interessati, ovvero quelli che sono in grado di accettare un valore per il parametro "InputObject" dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="a7724-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="a7724-109">Se questo valore non viene passato dalla pipeline, il cmdlet non verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="a7724-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="a7724-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="a7724-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="a7724-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="a7724-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="a7724-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="a7724-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="a7724-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="a7724-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="a7724-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="a7724-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="a7724-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="a7724-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="a7724-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="a7724-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="a7724-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="a7724-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="a7724-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="a7724-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="a7724-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="a7724-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="a7724-120">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="a7724-120">Resolution</span></span>

<span data-ttu-id="a7724-121">I cmdlet funzionano correttamente quando il valore del parametro InputObject viene passato dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="a7724-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="a7724-122">Di seguito sono riportati alcuni esempi di valori corretti per i cmdlet indicati in precedenza:</span><span class="sxs-lookup"><span data-stu-id="a7724-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```