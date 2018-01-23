---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9f512-103">Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9f512-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9f512-104">Chiama direttamente il metodo di **Get** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="9f512-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="9f512-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9f512-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="9f512-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9f512-106">Parameters</span></span>
----------

<span data-ttu-id="9f512-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9f512-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="9f512-108">Il nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="9f512-108">The name of the resource to call.</span></span>

<span data-ttu-id="9f512-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9f512-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="9f512-110">Il nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="9f512-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="9f512-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9f512-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="9f512-112">Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="9f512-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="9f512-113">Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="9f512-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="9f512-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9f512-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="9f512-115">In fase di restituzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="9f512-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="9f512-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9f512-116">Return value</span></span>
------------

<span data-ttu-id="9f512-117">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="9f512-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f512-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9f512-118">Remarks</span></span>

<span data-ttu-id="9f512-119">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="9f512-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f512-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9f512-120">Requirements</span></span>
------------
><span data-ttu-id="9f512-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9f512-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9f512-122">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9f512-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9f512-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9f512-123">See also</span></span>


[<span data-ttu-id="9f512-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9f512-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



