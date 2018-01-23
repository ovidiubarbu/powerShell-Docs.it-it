---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0ee2f-103">Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0ee2f-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0ee2f-104">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="0ee2f-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="0ee2f-105">Se non sono presenti configurazioni in sospeso, questo metodo applica nuovamente la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="0ee2f-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="0ee2f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0ee2f-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0ee2f-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="0ee2f-107">Parameters</span></span>
----------

<span data-ttu-id="0ee2f-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0ee2f-108">*force* \[in\]</span></span>  
<span data-ttu-id="0ee2f-109">Se il valore è **true**, la configurazione corrente viene applicata nuovamente, anche se è presente una configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="0ee2f-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="0ee2f-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0ee2f-110">Return value</span></span>
------------

<span data-ttu-id="0ee2f-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="0ee2f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ee2f-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="0ee2f-112">Remarks</span></span>

<span data-ttu-id="0ee2f-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="0ee2f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ee2f-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0ee2f-114">Requirements</span></span>
------------
><span data-ttu-id="0ee2f-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0ee2f-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0ee2f-116">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0ee2f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0ee2f-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ee2f-117">See also</span></span>


[<span data-ttu-id="0ee2f-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0ee2f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



