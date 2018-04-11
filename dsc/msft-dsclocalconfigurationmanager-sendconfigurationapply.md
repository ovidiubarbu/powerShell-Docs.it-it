---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8edf8c55089e767394ba21b42fe74072777a45c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="69e01-103">Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="69e01-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="69e01-104">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="69e01-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="69e01-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69e01-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="69e01-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="69e01-106">Parameters</span></span>
----------

<span data-ttu-id="69e01-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="69e01-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="69e01-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="69e01-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="69e01-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="69e01-109">Return value</span></span>
------------

<span data-ttu-id="69e01-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="69e01-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="69e01-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="69e01-111">Remarks</span></span>

<span data-ttu-id="69e01-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="69e01-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="69e01-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="69e01-113">Requirements</span></span>
------------
><span data-ttu-id="69e01-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="69e01-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="69e01-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="69e01-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="69e01-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69e01-116">See also</span></span>


[<span data-ttu-id="69e01-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="69e01-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)