---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2c055b3fab468f85c9e2f91cf1eaf1a4353b4660
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f070d-103">Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f070d-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f070d-104">Chiama direttamente il metodo di **Get** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="f070d-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="f070d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f070d-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="f070d-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="f070d-106">Parameters</span></span>
----------

<span data-ttu-id="f070d-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f070d-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="f070d-108">Il nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="f070d-108">The name of the resource to call.</span></span>

<span data-ttu-id="f070d-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f070d-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="f070d-110">Il nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="f070d-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f070d-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f070d-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="f070d-112">Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="f070d-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f070d-113">Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="f070d-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f070d-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="f070d-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="f070d-115">In fase di restituzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="f070d-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="f070d-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f070d-116">Return value</span></span>
------------

<span data-ttu-id="f070d-117">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="f070d-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f070d-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f070d-118">Remarks</span></span>

<span data-ttu-id="f070d-119">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="f070d-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f070d-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f070d-120">Requirements</span></span>
------------
><span data-ttu-id="f070d-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f070d-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f070d-122">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f070d-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f070d-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f070d-123">See also</span></span>


[<span data-ttu-id="f070d-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f070d-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



