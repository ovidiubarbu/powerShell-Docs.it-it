---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e5a2b-103">Metodo RollBack della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e5a2b-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e5a2b-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="e5a2b-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="e5a2b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e5a2b-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="e5a2b-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="e5a2b-106">Parameters</span></span>
----------

<span data-ttu-id="e5a2b-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e5a2b-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="e5a2b-108">Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="e5a2b-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e5a2b-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e5a2b-109">Return value</span></span>
------------

<span data-ttu-id="e5a2b-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="e5a2b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5a2b-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e5a2b-111">Remarks</span></span>

<span data-ttu-id="e5a2b-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="e5a2b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5a2b-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e5a2b-113">Requirements</span></span>
------------
><span data-ttu-id="e5a2b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e5a2b-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e5a2b-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5a2b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e5a2b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e5a2b-116">See also</span></span>


[<span data-ttu-id="e5a2b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e5a2b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



