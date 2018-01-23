---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9aebe-103">Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9aebe-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9aebe-104">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="9aebe-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="9aebe-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9aebe-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="9aebe-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9aebe-106">Parameters</span></span>
----------

<span data-ttu-id="9aebe-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9aebe-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="9aebe-108">Specifica i dati di configurazione da inviare.</span><span class="sxs-lookup"><span data-stu-id="9aebe-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="9aebe-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9aebe-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="9aebe-110">In fase di restituzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="9aebe-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="9aebe-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9aebe-111">Return value</span></span>
------------

<span data-ttu-id="9aebe-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="9aebe-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9aebe-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9aebe-113">Remarks</span></span>

<span data-ttu-id="9aebe-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="9aebe-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9aebe-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9aebe-115">Requirements</span></span>
------------
><span data-ttu-id="9aebe-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9aebe-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9aebe-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9aebe-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9aebe-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9aebe-118">See also</span></span>


[<span data-ttu-id="9aebe-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9aebe-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



