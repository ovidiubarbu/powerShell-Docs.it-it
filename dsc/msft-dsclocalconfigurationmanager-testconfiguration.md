---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5a5fd-103">Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5a5fd-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5a5fd-104">Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="5a5fd-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5a5fd-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="5a5fd-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="5a5fd-106">Parameters</span></span>
----------

<span data-ttu-id="5a5fd-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5a5fd-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="5a5fd-108">Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="5a5fd-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5a5fd-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="5a5fd-110">In fase di restituzione, specifica se il nodo gestito è nello stato specificato dal documento di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="5a5fd-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5a5fd-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="5a5fd-112">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceInDesiredState** che specifica le risorse che si trovano nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="5a5fd-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5a5fd-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="5a5fd-114">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceNotInDesiredState** che specifica le risorse che non si trovano nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a5fd-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5a5fd-115">Return value</span></span>
------------

<span data-ttu-id="5a5fd-116">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a5fd-117">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5a5fd-117">Remarks</span></span>

<span data-ttu-id="5a5fd-118">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="5a5fd-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a5fd-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5a5fd-119">Requirements</span></span>
------------
><span data-ttu-id="5a5fd-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5a5fd-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5a5fd-121">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a5fd-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5a5fd-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a5fd-122">See also</span></span>


[<span data-ttu-id="5a5fd-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5a5fd-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



