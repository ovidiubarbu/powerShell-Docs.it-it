---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ApplyConfiguration
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953458"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="8615e-103">Metodo ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="8615e-103">ApplyConfiguration method</span></span>

<span data-ttu-id="8615e-104">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="8615e-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="8615e-105">Se non sono presenti configurazioni in sospeso, questo metodo applica nuovamente la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="8615e-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8615e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8615e-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8615e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="8615e-107">Parameters</span></span>

<span data-ttu-id="8615e-108">*force* \[in\] Se il valore è **true**, la configurazione corrente viene applicata nuovamente, anche se è presente una configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="8615e-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="8615e-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8615e-109">Return value</span></span>

<span data-ttu-id="8615e-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="8615e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8615e-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8615e-111">Remarks</span></span>

<span data-ttu-id="8615e-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="8615e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8615e-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8615e-113">Requirements</span></span>

<span data-ttu-id="8615e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8615e-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8615e-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8615e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8615e-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8615e-116">See also</span></span>

[<span data-ttu-id="8615e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8615e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
