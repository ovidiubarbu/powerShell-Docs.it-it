---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5ff27-103">Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5ff27-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5ff27-104">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5ff27-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="5ff27-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5ff27-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="5ff27-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="5ff27-106">Parameters</span></span>
----------

<span data-ttu-id="5ff27-107">*Stage* \[in\] Specifica il documento di configurazione da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="5ff27-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="5ff27-108">I valori validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="5ff27-108">The following values are valid:</span></span>

|<span data-ttu-id="5ff27-109">Value</span><span class="sxs-lookup"><span data-stu-id="5ff27-109">Value</span></span> |<span data-ttu-id="5ff27-110">Description</span><span class="sxs-lookup"><span data-stu-id="5ff27-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5ff27-111">**1**</span><span class="sxs-lookup"><span data-stu-id="5ff27-111">**1**</span></span> | <span data-ttu-id="5ff27-112">Il documento di configurazione **corrente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="5ff27-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="5ff27-113">**2**</span><span class="sxs-lookup"><span data-stu-id="5ff27-113">**2**</span></span> | <span data-ttu-id="5ff27-114">Il documento di configurazione **in sospeso** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="5ff27-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="5ff27-115">**4**</span><span class="sxs-lookup"><span data-stu-id="5ff27-115">**4**</span></span> | <span data-ttu-id="5ff27-116">Il documento di configurazione **precedente** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="5ff27-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="5ff27-117">*Force* \[in\] **true** per forzare la rimozione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="5ff27-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ff27-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5ff27-118">Return value</span></span>
------------

<span data-ttu-id="5ff27-119">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="5ff27-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ff27-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5ff27-120">Remarks</span></span>

<span data-ttu-id="5ff27-121">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="5ff27-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ff27-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5ff27-122">Requirements</span></span>
------------
><span data-ttu-id="5ff27-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5ff27-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5ff27-124">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ff27-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5ff27-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ff27-125">See also</span></span>


[<span data-ttu-id="5ff27-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5ff27-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)