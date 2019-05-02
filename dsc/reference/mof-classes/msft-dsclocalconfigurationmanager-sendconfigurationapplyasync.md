---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078278"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="791d1-103">Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="791d1-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="791d1-104">Invia il documento di configurazione in modo asicrono al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="791d1-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="791d1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="791d1-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="791d1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="791d1-106">Parameters</span></span>

<span data-ttu-id="791d1-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="791d1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="791d1-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="791d1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="791d1-109">*jobId* \[in\] ID del processo per cui inviare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="791d1-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="791d1-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="791d1-110">Return value</span></span>

<span data-ttu-id="791d1-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="791d1-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="791d1-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="791d1-112">Remarks</span></span>

<span data-ttu-id="791d1-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="791d1-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="791d1-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="791d1-114">Requirements</span></span>

<span data-ttu-id="791d1-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="791d1-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="791d1-116">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="791d1-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="791d1-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="791d1-117">See also</span></span>

[<span data-ttu-id="791d1-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="791d1-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)