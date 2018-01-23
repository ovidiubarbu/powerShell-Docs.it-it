---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e9428-103">Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e9428-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e9428-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="e9428-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="e9428-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e9428-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="e9428-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="e9428-106">Parameters</span></span>
----------

<span data-ttu-id="e9428-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e9428-107">*force* \[in\]</span></span>  
<span data-ttu-id="e9428-108">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="e9428-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e9428-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e9428-109">Return value</span></span>
------------

<span data-ttu-id="e9428-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="e9428-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9428-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e9428-111">Remarks</span></span>

<span data-ttu-id="e9428-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="e9428-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9428-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e9428-113">Requirements</span></span>
------------
><span data-ttu-id="e9428-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e9428-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e9428-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9428-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e9428-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e9428-116">See also</span></span>


[<span data-ttu-id="e9428-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e9428-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



