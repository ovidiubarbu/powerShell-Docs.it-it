---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726995"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="18815-103">Metodo StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="18815-103">StopConfiguration method</span></span>

<span data-ttu-id="18815-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="18815-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="18815-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="18815-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="18815-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="18815-106">Parameters</span></span>

<span data-ttu-id="18815-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="18815-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="18815-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="18815-108">Return value</span></span>

<span data-ttu-id="18815-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="18815-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18815-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="18815-110">Remarks</span></span>

<span data-ttu-id="18815-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="18815-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18815-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="18815-112">Requirements</span></span>

<span data-ttu-id="18815-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18815-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="18815-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18815-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="18815-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="18815-115">See also</span></span>

[<span data-ttu-id="18815-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18815-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
