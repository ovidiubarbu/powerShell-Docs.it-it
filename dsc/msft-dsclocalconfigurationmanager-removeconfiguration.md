---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3ab30-103">Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3ab30-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3ab30-104">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="3ab30-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="3ab30-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3ab30-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="3ab30-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="3ab30-106">Parameters</span></span>
----------

<span data-ttu-id="3ab30-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3ab30-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="3ab30-108">Specifica il documento di configurazione da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="3ab30-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="3ab30-109">I valori validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="3ab30-109">The following values are valid:</span></span>

|<span data-ttu-id="3ab30-110">Value</span><span class="sxs-lookup"><span data-stu-id="3ab30-110">Value</span></span> |<span data-ttu-id="3ab30-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3ab30-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="3ab30-112">**1**</span><span class="sxs-lookup"><span data-stu-id="3ab30-112">**1**</span></span> | <span data-ttu-id="3ab30-113">Il documento di configurazione **corrente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="3ab30-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="3ab30-114">**2**</span><span class="sxs-lookup"><span data-stu-id="3ab30-114">**2**</span></span> | <span data-ttu-id="3ab30-115">Il documento di configurazione **in sospeso** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="3ab30-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="3ab30-116">**4**</span><span class="sxs-lookup"><span data-stu-id="3ab30-116">**4**</span></span> | <span data-ttu-id="3ab30-117">Il documento di configurazione **precedente** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="3ab30-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="3ab30-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3ab30-118">*Force* \[in\]</span></span>  
<span data-ttu-id="3ab30-119">**true** per forzare la rimozione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="3ab30-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ab30-120">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3ab30-120">Return value</span></span>
------------

<span data-ttu-id="3ab30-121">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="3ab30-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ab30-122">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3ab30-122">Remarks</span></span>

<span data-ttu-id="3ab30-123">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="3ab30-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ab30-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3ab30-124">Requirements</span></span>
------------
><span data-ttu-id="3ab30-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3ab30-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3ab30-126">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ab30-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3ab30-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3ab30-127">See also</span></span>


[<span data-ttu-id="3ab30-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ab30-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



