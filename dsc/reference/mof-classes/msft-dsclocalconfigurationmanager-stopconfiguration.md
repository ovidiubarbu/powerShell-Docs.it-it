---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682219"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3b525-103">Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3b525-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3b525-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="3b525-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b525-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3b525-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3b525-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="3b525-106">Parameters</span></span>

<span data-ttu-id="3b525-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="3b525-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3b525-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3b525-108">Return value</span></span>

<span data-ttu-id="3b525-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="3b525-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b525-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3b525-110">Remarks</span></span>

<span data-ttu-id="3b525-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="3b525-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b525-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3b525-112">Requirements</span></span>

<span data-ttu-id="3b525-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3b525-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3b525-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3b525-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3b525-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b525-115">See also</span></span>

[<span data-ttu-id="3b525-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3b525-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)