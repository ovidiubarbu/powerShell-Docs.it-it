---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="007a1-103">Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="007a1-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="007a1-104">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="007a1-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="007a1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="007a1-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="007a1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="007a1-106">Parameters</span></span>
----------

<span data-ttu-id="007a1-107">*configurationData* \[in\] Specifica i dati di configurazione da inviare.</span><span class="sxs-lookup"><span data-stu-id="007a1-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="007a1-108">*configurations* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="007a1-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="007a1-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="007a1-109">Return value</span></span>
------------

<span data-ttu-id="007a1-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="007a1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="007a1-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="007a1-111">Remarks</span></span>

<span data-ttu-id="007a1-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="007a1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="007a1-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="007a1-113">Requirements</span></span>
------------
><span data-ttu-id="007a1-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="007a1-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="007a1-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="007a1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="007a1-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="007a1-116">See also</span></span>


[<span data-ttu-id="007a1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="007a1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)