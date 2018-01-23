---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="075ff-103">Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="075ff-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="075ff-104">Invia il documento di configurazione in modo asicrono al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="075ff-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="075ff-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="075ff-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="075ff-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="075ff-106">Parameters</span></span>
----------

<span data-ttu-id="075ff-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="075ff-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="075ff-108">I dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="075ff-108">The environment data for the configuration.</span></span>

<span data-ttu-id="075ff-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="075ff-109">*force* \[in\]</span></span>  
<span data-ttu-id="075ff-110">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="075ff-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="075ff-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="075ff-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="075ff-112">L'ID del processo per cui inviare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="075ff-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="075ff-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="075ff-113">Return value</span></span>
------------

<span data-ttu-id="075ff-114">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="075ff-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="075ff-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="075ff-115">Remarks</span></span>

<span data-ttu-id="075ff-116">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="075ff-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="075ff-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="075ff-117">Requirements</span></span>
------------
><span data-ttu-id="075ff-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="075ff-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="075ff-119">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="075ff-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="075ff-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="075ff-120">See also</span></span>


[<span data-ttu-id="075ff-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="075ff-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



