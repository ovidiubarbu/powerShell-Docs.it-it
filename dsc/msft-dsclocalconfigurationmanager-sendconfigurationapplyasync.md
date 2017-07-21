---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="568ef-103">Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="568ef-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="568ef-104">Invia il documento di configurazione in modo asicrono al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="568ef-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="568ef-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="568ef-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="568ef-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="568ef-106">Parameters</span></span>
----------

<span data-ttu-id="568ef-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="568ef-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="568ef-108">I dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="568ef-108">The environment data for the configuration.</span></span>

<span data-ttu-id="568ef-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="568ef-109">*force* \[in\]</span></span>  
<span data-ttu-id="568ef-110">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="568ef-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="568ef-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="568ef-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="568ef-112">L'ID del processo per cui inviare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="568ef-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="568ef-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="568ef-113">Return value</span></span>
------------

<span data-ttu-id="568ef-114">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="568ef-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="568ef-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="568ef-115">Remarks</span></span>

<span data-ttu-id="568ef-116">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="568ef-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="568ef-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="568ef-117">Requirements</span></span>
------------
><span data-ttu-id="568ef-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="568ef-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="568ef-119">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="568ef-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="568ef-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="568ef-120">See also</span></span>


[<span data-ttu-id="568ef-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="568ef-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



