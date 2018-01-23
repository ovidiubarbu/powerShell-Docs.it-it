---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4318b-103">Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4318b-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4318b-104">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4318b-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="4318b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4318b-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4318b-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="4318b-106">Parameters</span></span>
----------

<span data-ttu-id="4318b-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4318b-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="4318b-108">I dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4318b-108">The environment data for the configuration.</span></span>

<span data-ttu-id="4318b-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4318b-109">*force* \[in\]</span></span>  
<span data-ttu-id="4318b-110">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="4318b-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4318b-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4318b-111">Return value</span></span>
------------

<span data-ttu-id="4318b-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="4318b-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4318b-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4318b-113">Remarks</span></span>

<span data-ttu-id="4318b-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="4318b-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4318b-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4318b-115">Requirements</span></span>
------------
><span data-ttu-id="4318b-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4318b-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4318b-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4318b-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4318b-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4318b-118">See also</span></span>


[<span data-ttu-id="4318b-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4318b-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



