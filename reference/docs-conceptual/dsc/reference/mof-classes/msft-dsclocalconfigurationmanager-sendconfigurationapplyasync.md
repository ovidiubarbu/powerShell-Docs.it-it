---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApplyAsync
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953378"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="a2473-103">Metodo SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="a2473-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="a2473-104">Invia il documento di configurazione in modo asicrono al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="a2473-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2473-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a2473-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="a2473-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="a2473-106">Parameters</span></span>

<span data-ttu-id="a2473-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="a2473-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a2473-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="a2473-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="a2473-109">*jobId* \[in\] ID del processo per cui inviare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="a2473-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2473-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="a2473-110">Return value</span></span>

<span data-ttu-id="a2473-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="a2473-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2473-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a2473-112">Remarks</span></span>

<span data-ttu-id="a2473-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="a2473-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2473-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a2473-114">Requirements</span></span>

<span data-ttu-id="a2473-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a2473-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a2473-116">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a2473-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a2473-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a2473-117">See also</span></span>

[<span data-ttu-id="a2473-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a2473-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
