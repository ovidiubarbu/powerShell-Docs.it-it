---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
contributor: vaibch
title: Errore dei cmdlet per la gestione dei commutatori di rete
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="05ba0-103">Questi cmdlet consentono di gestire i commutatori di rete su WS-Management.</span><span class="sxs-lookup"><span data-stu-id="05ba0-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="05ba0-104">Alcuni cmdlet di questo modulo sono in grado di accettare i valori dalle pipeline.</span><span class="sxs-lookup"><span data-stu-id="05ba0-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="05ba0-105">In WMF 5.1 (anteprima) i cmdlet di questo tipo non vengono eseguiti quando le pipeline non permettono il passaggio dei valori.</span><span class="sxs-lookup"><span data-stu-id="05ba0-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="05ba0-106">Se non viene usato il parametro "InputObject", l'esecuzione del cmdlet dovrebbe continuare senza errori.</span><span class="sxs-lookup"><span data-stu-id="05ba0-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="05ba0-107">Di seguito è riportato l'elenco dei cmdlet interessati, ovvero quelli che sono in grado di accettare un valore per il parametro "InputObject" dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="05ba0-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="05ba0-108">Se questo valore non viene passato dalla pipeline, il cmdlet non verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="05ba0-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="05ba0-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="05ba0-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="05ba0-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="05ba0-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="05ba0-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="05ba0-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="05ba0-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="05ba0-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="05ba0-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="05ba0-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="05ba0-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="05ba0-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="05ba0-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="05ba0-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="05ba0-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="05ba0-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="05ba0-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="05ba0-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="05ba0-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="05ba0-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="05ba0-119">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="05ba0-119">Resolution</span></span>
<span data-ttu-id="05ba0-120">I cmdlet funzionano correttamente quando il valore del parametro InputObject viene passato dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="05ba0-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="05ba0-121">Di seguito sono riportati alcuni esempi di valori corretti per i cmdlet indicati in precedenza:</span><span class="sxs-lookup"><span data-stu-id="05ba0-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="05ba0-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="05ba0-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="05ba0-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="05ba0-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="05ba0-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="05ba0-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="05ba0-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="05ba0-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="05ba0-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="05ba0-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="05ba0-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="05ba0-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="05ba0-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="05ba0-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="05ba0-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="05ba0-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```