---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24536-103">Metodo RollBack della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24536-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24536-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="24536-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="24536-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="24536-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="24536-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="24536-106">Parameters</span></span>
----------

<span data-ttu-id="24536-107">*configurationNumber* \[in\] Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="24536-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="24536-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="24536-108">Return value</span></span>
------------

<span data-ttu-id="24536-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="24536-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24536-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="24536-110">Remarks</span></span>

<span data-ttu-id="24536-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="24536-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24536-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="24536-112">Requirements</span></span>
------------
><span data-ttu-id="24536-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24536-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="24536-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24536-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="24536-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24536-115">See also</span></span>


[<span data-ttu-id="24536-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24536-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)