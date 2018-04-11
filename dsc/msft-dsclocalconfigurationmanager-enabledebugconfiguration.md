---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="86f9a-103">Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="86f9a-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="86f9a-104">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="86f9a-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="86f9a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="86f9a-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="86f9a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="86f9a-106">Parameters</span></span>
----------

<span data-ttu-id="86f9a-107">*BreakAll* \[in\] Imposta un punto di interruzione su ogni riga nello script della risorsa.</span><span class="sxs-lookup"><span data-stu-id="86f9a-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="86f9a-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="86f9a-108">Return value</span></span>
------------

<span data-ttu-id="86f9a-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="86f9a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="86f9a-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="86f9a-110">Remarks</span></span>

<span data-ttu-id="86f9a-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="86f9a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="86f9a-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="86f9a-112">Requirements</span></span>
------------
><span data-ttu-id="86f9a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="86f9a-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="86f9a-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="86f9a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="86f9a-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="86f9a-115">See also</span></span>


[<span data-ttu-id="86f9a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="86f9a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)