---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="73189-103">Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="73189-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="73189-104">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="73189-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="73189-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="73189-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="73189-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="73189-106">Parameters</span></span>
----------

<span data-ttu-id="73189-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="73189-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="73189-108">Specifica i dati di configurazione da inviare.</span><span class="sxs-lookup"><span data-stu-id="73189-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="73189-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="73189-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="73189-110">In fase di restituzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="73189-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="73189-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="73189-111">Return value</span></span>
------------

<span data-ttu-id="73189-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="73189-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="73189-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="73189-113">Remarks</span></span>

<span data-ttu-id="73189-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="73189-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="73189-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="73189-115">Requirements</span></span>
------------
><span data-ttu-id="73189-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="73189-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="73189-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="73189-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="73189-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="73189-118">See also</span></span>


[<span data-ttu-id="73189-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="73189-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



