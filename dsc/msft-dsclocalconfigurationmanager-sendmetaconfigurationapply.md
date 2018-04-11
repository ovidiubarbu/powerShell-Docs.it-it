---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="76e22-103">Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="76e22-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="76e22-104">Consente di configurare le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="76e22-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="76e22-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="76e22-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="76e22-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="76e22-106">Parameters</span></span>
----------

<span data-ttu-id="76e22-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="76e22-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="76e22-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="76e22-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="76e22-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="76e22-109">Return value</span></span>
------------

<span data-ttu-id="76e22-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="76e22-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="76e22-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="76e22-111">Remarks</span></span>

<span data-ttu-id="76e22-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="76e22-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="76e22-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="76e22-113">Requirements</span></span>
------------
><span data-ttu-id="76e22-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="76e22-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="76e22-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="76e22-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="76e22-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="76e22-116">See also</span></span>


[<span data-ttu-id="76e22-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="76e22-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)