---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e8ed4-103">Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e8ed4-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e8ed4-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="e8ed4-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="e8ed4-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e8ed4-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="e8ed4-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="e8ed4-106">Parameters</span></span>
----------

<span data-ttu-id="e8ed4-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e8ed4-107">*force* \[in\]</span></span>  
<span data-ttu-id="e8ed4-108">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="e8ed4-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8ed4-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e8ed4-109">Return value</span></span>
------------

<span data-ttu-id="e8ed4-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="e8ed4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8ed4-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e8ed4-111">Remarks</span></span>

<span data-ttu-id="e8ed4-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="e8ed4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8ed4-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e8ed4-113">Requirements</span></span>
------------
><span data-ttu-id="e8ed4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e8ed4-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e8ed4-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8ed4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e8ed4-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e8ed4-116">See also</span></span>


[<span data-ttu-id="e8ed4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e8ed4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



