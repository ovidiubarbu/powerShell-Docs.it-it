---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047508"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5406b-103">Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5406b-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5406b-104">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5406b-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="5406b-105">Se non sono presenti configurazioni in sospeso, questo metodo applica nuovamente la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="5406b-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="5406b-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5406b-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5406b-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="5406b-107">Parameters</span></span>

<span data-ttu-id="5406b-108">*force* \[in\] Se il valore è **true**, la configurazione corrente viene applicata nuovamente, anche se è presente una configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5406b-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="5406b-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5406b-109">Return value</span></span>

<span data-ttu-id="5406b-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="5406b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5406b-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5406b-111">Remarks</span></span>

<span data-ttu-id="5406b-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="5406b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5406b-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5406b-113">Requirements</span></span>

<span data-ttu-id="5406b-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5406b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5406b-115">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5406b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5406b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5406b-116">See also</span></span>

[<span data-ttu-id="5406b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5406b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)