---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8fec9-103">Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8fec9-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8fec9-104">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="8fec9-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="8fec9-105">Se non sono presenti configurazioni in sospeso, questo metodo applica nuovamente la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="8fec9-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="8fec9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8fec9-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8fec9-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8fec9-107">Parameters</span></span>
----------

<span data-ttu-id="8fec9-108">*force* \[in\] Se il valore è **true**, la configurazione corrente viene applicata nuovamente, anche se è presente una configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="8fec9-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="8fec9-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8fec9-109">Return value</span></span>
------------

<span data-ttu-id="8fec9-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="8fec9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fec9-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8fec9-111">Remarks</span></span>

<span data-ttu-id="8fec9-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="8fec9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8fec9-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8fec9-113">Requirements</span></span>
------------
><span data-ttu-id="8fec9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8fec9-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8fec9-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8fec9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8fec9-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8fec9-116">See also</span></span>


[<span data-ttu-id="8fec9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8fec9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)