---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953358"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="eb4ca-103">Metodo StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb4ca-103">StopConfiguration method</span></span>

<span data-ttu-id="eb4ca-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="eb4ca-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb4ca-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="eb4ca-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="eb4ca-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="eb4ca-106">Parameters</span></span>

<span data-ttu-id="eb4ca-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="eb4ca-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="eb4ca-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="eb4ca-108">Return value</span></span>

<span data-ttu-id="eb4ca-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="eb4ca-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb4ca-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="eb4ca-110">Remarks</span></span>

<span data-ttu-id="eb4ca-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="eb4ca-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb4ca-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="eb4ca-112">Requirements</span></span>

<span data-ttu-id="eb4ca-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="eb4ca-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="eb4ca-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb4ca-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="eb4ca-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eb4ca-115">See also</span></span>

[<span data-ttu-id="eb4ca-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="eb4ca-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
