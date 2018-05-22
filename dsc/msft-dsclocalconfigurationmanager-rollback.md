---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="78957-103">Metodo RollBack della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="78957-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="78957-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="78957-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="78957-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="78957-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="78957-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="78957-106">Parameters</span></span>
----------

<span data-ttu-id="78957-107">*configurationNumber* \[in\] Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="78957-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="78957-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="78957-108">Return value</span></span>
------------

<span data-ttu-id="78957-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="78957-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78957-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="78957-110">Remarks</span></span>

<span data-ttu-id="78957-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="78957-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78957-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="78957-112">Requirements</span></span>
------------
><span data-ttu-id="78957-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78957-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="78957-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78957-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="78957-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="78957-115">See also</span></span>


[<span data-ttu-id="78957-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="78957-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)