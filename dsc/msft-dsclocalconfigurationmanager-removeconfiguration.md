---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="780e4-103">Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="780e4-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="780e4-104">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="780e4-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="780e4-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="780e4-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="780e4-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="780e4-106">Parameters</span></span>
----------

<span data-ttu-id="780e4-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="780e4-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="780e4-108">Specifica il documento di configurazione da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="780e4-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="780e4-109">I valori validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="780e4-109">The following values are valid:</span></span>

|<span data-ttu-id="780e4-110">Value</span><span class="sxs-lookup"><span data-stu-id="780e4-110">Value</span></span> |<span data-ttu-id="780e4-111">Description</span><span class="sxs-lookup"><span data-stu-id="780e4-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="780e4-112">**1**</span><span class="sxs-lookup"><span data-stu-id="780e4-112">**1**</span></span> | <span data-ttu-id="780e4-113">Il documento di configurazione **corrente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="780e4-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="780e4-114">**2**</span><span class="sxs-lookup"><span data-stu-id="780e4-114">**2**</span></span> | <span data-ttu-id="780e4-115">Il documento di configurazione **in sospeso** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="780e4-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="780e4-116">**4**</span><span class="sxs-lookup"><span data-stu-id="780e4-116">**4**</span></span> | <span data-ttu-id="780e4-117">Il documento di configurazione **precedente** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="780e4-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="780e4-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="780e4-118">*Force* \[in\]</span></span>  
<span data-ttu-id="780e4-119">**true** per forzare la rimozione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="780e4-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="780e4-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="780e4-120">Return value</span></span>
------------

<span data-ttu-id="780e4-121">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="780e4-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="780e4-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="780e4-122">Remarks</span></span>

<span data-ttu-id="780e4-123">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="780e4-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="780e4-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="780e4-124">Requirements</span></span>
------------
><span data-ttu-id="780e4-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="780e4-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="780e4-126">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="780e4-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="780e4-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="780e4-127">See also</span></span>


[<span data-ttu-id="780e4-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="780e4-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



