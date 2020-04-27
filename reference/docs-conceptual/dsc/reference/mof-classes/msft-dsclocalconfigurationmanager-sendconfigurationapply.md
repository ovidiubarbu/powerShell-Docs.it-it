---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApply
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954888"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="c5d06-103">Metodo SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="c5d06-103">SendConfigurationApply method</span></span>

<span data-ttu-id="c5d06-104">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c5d06-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5d06-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c5d06-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c5d06-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="c5d06-106">Parameters</span></span>

<span data-ttu-id="c5d06-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c5d06-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c5d06-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="c5d06-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c5d06-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c5d06-109">Return value</span></span>

<span data-ttu-id="c5d06-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="c5d06-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5d06-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c5d06-111">Remarks</span></span>

<span data-ttu-id="c5d06-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="c5d06-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5d06-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c5d06-113">Requirements</span></span>

<span data-ttu-id="c5d06-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c5d06-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c5d06-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5d06-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c5d06-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c5d06-116">See also</span></span>

[<span data-ttu-id="c5d06-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c5d06-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
