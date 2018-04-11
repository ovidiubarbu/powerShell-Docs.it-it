---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9978e-103">Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9978e-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9978e-104">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9978e-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="9978e-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9978e-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="9978e-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9978e-106">Parameters</span></span>
----------

<span data-ttu-id="9978e-107">*Stage* \[in\] Specifica il documento di configurazione da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="9978e-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="9978e-108">I valori validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="9978e-108">The following values are valid:</span></span>

|<span data-ttu-id="9978e-109">Value</span><span class="sxs-lookup"><span data-stu-id="9978e-109">Value</span></span> |<span data-ttu-id="9978e-110">Description</span><span class="sxs-lookup"><span data-stu-id="9978e-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="9978e-111">**1**</span><span class="sxs-lookup"><span data-stu-id="9978e-111">**1**</span></span> | <span data-ttu-id="9978e-112">Il documento di configurazione **corrente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="9978e-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="9978e-113">**2**</span><span class="sxs-lookup"><span data-stu-id="9978e-113">**2**</span></span> | <span data-ttu-id="9978e-114">Il documento di configurazione **in sospeso** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="9978e-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="9978e-115">**4**</span><span class="sxs-lookup"><span data-stu-id="9978e-115">**4**</span></span> | <span data-ttu-id="9978e-116">Il documento di configurazione **precedente** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="9978e-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="9978e-117">*Force* \[in\] **true** per forzare la rimozione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="9978e-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9978e-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9978e-118">Return value</span></span>
------------

<span data-ttu-id="9978e-119">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="9978e-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9978e-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9978e-120">Remarks</span></span>

<span data-ttu-id="9978e-121">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="9978e-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9978e-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9978e-122">Requirements</span></span>
------------
><span data-ttu-id="9978e-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9978e-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9978e-124">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9978e-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9978e-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9978e-125">See also</span></span>


[<span data-ttu-id="9978e-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9978e-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)