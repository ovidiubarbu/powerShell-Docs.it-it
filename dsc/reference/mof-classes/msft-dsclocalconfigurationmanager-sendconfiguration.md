---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfiguration
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734318"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="5af1d-103">Metodo SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="5af1d-103">SendConfiguration method</span></span>

<span data-ttu-id="5af1d-104">Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5af1d-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="5af1d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5af1d-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5af1d-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="5af1d-106">Parameters</span></span>

<span data-ttu-id="5af1d-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5af1d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="5af1d-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="5af1d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5af1d-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5af1d-109">Return value</span></span>

<span data-ttu-id="5af1d-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="5af1d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5af1d-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5af1d-111">Remarks</span></span>

<span data-ttu-id="5af1d-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="5af1d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5af1d-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5af1d-113">Requirements</span></span>

<span data-ttu-id="5af1d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5af1d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5af1d-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5af1d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5af1d-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5af1d-116">See also</span></span>

[<span data-ttu-id="5af1d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5af1d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
