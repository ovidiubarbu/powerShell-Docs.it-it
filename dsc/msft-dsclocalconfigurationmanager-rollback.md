---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="63cd7-103">Metodo RollBack della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="63cd7-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="63cd7-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="63cd7-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="63cd7-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="63cd7-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="63cd7-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="63cd7-106">Parameters</span></span>
----------

<span data-ttu-id="63cd7-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="63cd7-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="63cd7-108">Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="63cd7-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="63cd7-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="63cd7-109">Return value</span></span>
------------

<span data-ttu-id="63cd7-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="63cd7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="63cd7-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="63cd7-111">Remarks</span></span>

<span data-ttu-id="63cd7-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="63cd7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="63cd7-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="63cd7-113">Requirements</span></span>
------------
><span data-ttu-id="63cd7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="63cd7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="63cd7-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="63cd7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="63cd7-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="63cd7-116">See also</span></span>


[<span data-ttu-id="63cd7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="63cd7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



