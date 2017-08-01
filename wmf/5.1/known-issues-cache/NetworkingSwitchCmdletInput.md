---
title: Errore dei cmdlet per la gestione dei commutatori di rete
contributor: vaibch
ms.openlocfilehash: e32e31762b665a7e2c6f6938fe494cb6127d4264
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
<span data-ttu-id="5e788-102">Questi cmdlet consentono di gestire i commutatori di rete su WS-Management.</span><span class="sxs-lookup"><span data-stu-id="5e788-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="5e788-103">Alcuni cmdlet di questo modulo sono in grado di accettare i valori dalle pipeline.</span><span class="sxs-lookup"><span data-stu-id="5e788-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="5e788-104">In WMF 5.1 (anteprima) i cmdlet di questo tipo non vengono eseguiti quando le pipeline non permettono il passaggio dei valori.</span><span class="sxs-lookup"><span data-stu-id="5e788-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="5e788-105">Se non viene usato il parametro "InputObject", l'esecuzione del cmdlet dovrebbe continuare senza errori.</span><span class="sxs-lookup"><span data-stu-id="5e788-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="5e788-106">Di seguito è riportato l'elenco dei cmdlet interessati, ovvero quelli che sono in grado di accettare un valore per il parametro "InputObject" dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5e788-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="5e788-107">Se questo valore non viene passato dalla pipeline, il cmdlet non verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="5e788-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="5e788-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5e788-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="5e788-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5e788-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="5e788-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5e788-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="5e788-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5e788-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="5e788-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="5e788-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="5e788-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="5e788-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="5e788-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5e788-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="5e788-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5e788-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="5e788-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="5e788-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="5e788-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="5e788-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="5e788-118">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="5e788-118">Resolution</span></span>
<span data-ttu-id="5e788-119">I cmdlet funzionano correttamente quando il valore del parametro InputObject viene passato dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5e788-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="5e788-120">Di seguito sono riportati alcuni esempi di valori corretti per i cmdlet indicati in precedenza:</span><span class="sxs-lookup"><span data-stu-id="5e788-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="5e788-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5e788-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```
- <span data-ttu-id="5e788-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5e788-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="5e788-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5e788-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="5e788-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5e788-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="5e788-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="5e788-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="5e788-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5e788-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="5e788-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5e788-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="5e788-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="5e788-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
