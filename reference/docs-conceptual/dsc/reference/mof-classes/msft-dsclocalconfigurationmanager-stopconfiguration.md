---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953358"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="89f50-103">Metodo StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="89f50-103">StopConfiguration method</span></span>

<span data-ttu-id="89f50-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="89f50-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="89f50-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="89f50-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="89f50-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="89f50-106">Parameters</span></span>

<span data-ttu-id="89f50-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="89f50-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="89f50-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="89f50-108">Return value</span></span>

<span data-ttu-id="89f50-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="89f50-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="89f50-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="89f50-110">Remarks</span></span>

<span data-ttu-id="89f50-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="89f50-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="89f50-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="89f50-112">Requirements</span></span>

<span data-ttu-id="89f50-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="89f50-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="89f50-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="89f50-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="89f50-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89f50-115">See also</span></span>

[<span data-ttu-id="89f50-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="89f50-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
