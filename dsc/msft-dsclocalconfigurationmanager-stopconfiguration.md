---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ca621-103">Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ca621-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ca621-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="ca621-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="ca621-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ca621-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ca621-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="ca621-106">Parameters</span></span>
----------

<span data-ttu-id="ca621-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="ca621-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ca621-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ca621-108">Return value</span></span>
------------

<span data-ttu-id="ca621-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="ca621-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca621-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ca621-110">Remarks</span></span>

<span data-ttu-id="ca621-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="ca621-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca621-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ca621-112">Requirements</span></span>
------------
><span data-ttu-id="ca621-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ca621-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ca621-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca621-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ca621-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ca621-115">See also</span></span>


[<span data-ttu-id="ca621-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ca621-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)