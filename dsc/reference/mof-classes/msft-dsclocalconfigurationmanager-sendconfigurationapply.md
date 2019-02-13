---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678256"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="02d23-103">Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="02d23-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="02d23-104">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="02d23-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="02d23-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="02d23-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="02d23-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="02d23-106">Parameters</span></span>

<span data-ttu-id="02d23-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="02d23-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="02d23-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="02d23-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="02d23-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="02d23-109">Return value</span></span>

<span data-ttu-id="02d23-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="02d23-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="02d23-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="02d23-111">Remarks</span></span>

<span data-ttu-id="02d23-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="02d23-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="02d23-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="02d23-113">Requirements</span></span>

<span data-ttu-id="02d23-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="02d23-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="02d23-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="02d23-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="02d23-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="02d23-116">See also</span></span>

[<span data-ttu-id="02d23-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="02d23-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)