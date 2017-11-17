---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="68cfd-103">Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="68cfd-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="68cfd-104">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="68cfd-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="68cfd-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="68cfd-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="68cfd-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="68cfd-106">Parameters</span></span>
----------

<span data-ttu-id="68cfd-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="68cfd-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="68cfd-108">Imposta un punto di interruzione su ogni riga nello script della risorsa.</span><span class="sxs-lookup"><span data-stu-id="68cfd-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="68cfd-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="68cfd-109">Return value</span></span>
------------

<span data-ttu-id="68cfd-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="68cfd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="68cfd-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="68cfd-111">Remarks</span></span>

<span data-ttu-id="68cfd-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="68cfd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="68cfd-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="68cfd-113">Requirements</span></span>
------------
><span data-ttu-id="68cfd-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="68cfd-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="68cfd-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="68cfd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="68cfd-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68cfd-116">See also</span></span>


[<span data-ttu-id="68cfd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="68cfd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



