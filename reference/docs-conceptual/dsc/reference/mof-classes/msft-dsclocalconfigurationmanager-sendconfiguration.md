---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfiguration
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953388"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="d2667-103">Metodo SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2667-103">SendConfiguration method</span></span>

<span data-ttu-id="d2667-104">Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.</span><span class="sxs-lookup"><span data-stu-id="d2667-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2667-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d2667-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d2667-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="d2667-106">Parameters</span></span>

<span data-ttu-id="d2667-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="d2667-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d2667-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="d2667-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2667-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d2667-109">Return value</span></span>

<span data-ttu-id="d2667-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="d2667-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2667-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d2667-111">Remarks</span></span>

<span data-ttu-id="d2667-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="d2667-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2667-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d2667-113">Requirements</span></span>

<span data-ttu-id="d2667-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2667-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d2667-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2667-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d2667-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d2667-116">See also</span></span>

[<span data-ttu-id="d2667-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2667-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
