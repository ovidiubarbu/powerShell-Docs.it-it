---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="84962-103">Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="84962-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="84962-104">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="84962-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="84962-105">Se non sono presenti configurazioni in sospeso, questo metodo applica nuovamente la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="84962-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="84962-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="84962-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="84962-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="84962-107">Parameters</span></span>
----------

<span data-ttu-id="84962-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="84962-108">*force* \[in\]</span></span>  
<span data-ttu-id="84962-109">Se il valore è **true**, la configurazione corrente viene applicata nuovamente, anche se è presente una configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="84962-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="84962-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="84962-110">Return value</span></span>
------------

<span data-ttu-id="84962-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="84962-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="84962-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="84962-112">Remarks</span></span>

<span data-ttu-id="84962-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="84962-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="84962-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="84962-114">Requirements</span></span>
------------
><span data-ttu-id="84962-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="84962-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="84962-116">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="84962-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="84962-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="84962-117">See also</span></span>


[<span data-ttu-id="84962-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="84962-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



