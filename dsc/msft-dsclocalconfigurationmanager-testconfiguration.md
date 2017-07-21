---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8278b-103">Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8278b-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8278b-104">Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.</span><span class="sxs-lookup"><span data-stu-id="8278b-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="8278b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8278b-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="8278b-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="8278b-106">Parameters</span></span>
----------

<span data-ttu-id="8278b-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8278b-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="8278b-108">Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="8278b-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="8278b-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8278b-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="8278b-110">In fase di restituzione, specifica se il nodo gestito è nello stato specificato dal documento di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8278b-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="8278b-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8278b-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="8278b-112">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceInDesiredState** che specifica le risorse che si trovano nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="8278b-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="8278b-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8278b-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="8278b-114">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceNotInDesiredState** che specifica le risorse che non si trovano nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="8278b-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="8278b-115">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="8278b-115">Return value</span></span>
------------

<span data-ttu-id="8278b-116">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="8278b-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8278b-117">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8278b-117">Remarks</span></span>

<span data-ttu-id="8278b-118">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="8278b-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8278b-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8278b-119">Requirements</span></span>
------------
><span data-ttu-id="8278b-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8278b-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8278b-121">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8278b-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8278b-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8278b-122">See also</span></span>


[<span data-ttu-id="8278b-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8278b-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



