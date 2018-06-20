---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218876"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="94cb7-103">Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="94cb7-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="94cb7-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="94cb7-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="94cb7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="94cb7-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="94cb7-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="94cb7-106">Parameters</span></span>
----------

<span data-ttu-id="94cb7-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="94cb7-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="94cb7-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="94cb7-108">Return value</span></span>
------------

<span data-ttu-id="94cb7-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="94cb7-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="94cb7-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="94cb7-110">Remarks</span></span>

<span data-ttu-id="94cb7-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="94cb7-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94cb7-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="94cb7-112">Requirements</span></span>
------------
><span data-ttu-id="94cb7-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="94cb7-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="94cb7-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="94cb7-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="94cb7-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="94cb7-115">See also</span></span>


[<span data-ttu-id="94cb7-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="94cb7-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)