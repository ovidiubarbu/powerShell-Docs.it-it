---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendMetaConfigurationApply
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954878"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="bbf65-103">Metodo SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="bbf65-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="bbf65-104">Consente di configurare le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="bbf65-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="bbf65-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bbf65-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="bbf65-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="bbf65-106">Parameters</span></span>

<span data-ttu-id="bbf65-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="bbf65-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="bbf65-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="bbf65-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="bbf65-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="bbf65-109">Return value</span></span>

<span data-ttu-id="bbf65-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="bbf65-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbf65-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bbf65-111">Remarks</span></span>

<span data-ttu-id="bbf65-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="bbf65-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbf65-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bbf65-113">Requirements</span></span>

<span data-ttu-id="bbf65-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bbf65-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bbf65-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bbf65-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bbf65-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bbf65-116">See also</span></span>

[<span data-ttu-id="bbf65-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bbf65-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
