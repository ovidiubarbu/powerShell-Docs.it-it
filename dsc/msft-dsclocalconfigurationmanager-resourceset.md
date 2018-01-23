---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7291641098578226449f8cbd360da0a3f9842598
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="33be5-103">Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="33be5-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="33be5-104">Chiama direttamente il metodo di **Set** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="33be5-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="33be5-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="33be5-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="33be5-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="33be5-106">Parameters</span></span>
----------

<span data-ttu-id="33be5-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="33be5-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="33be5-108">Il nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="33be5-108">The name of the resource to call.</span></span>

<span data-ttu-id="33be5-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="33be5-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="33be5-110">Il nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="33be5-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="33be5-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="33be5-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="33be5-112">Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="33be5-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="33be5-113">Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="33be5-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="33be5-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="33be5-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="33be5-115">In fase di restituzione, questa proprietà è impostata su **true** se il nodo deve essere riavviato.</span><span class="sxs-lookup"><span data-stu-id="33be5-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="33be5-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="33be5-116">Return value</span></span>
------------

<span data-ttu-id="33be5-117">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="33be5-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="33be5-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="33be5-118">Remarks</span></span>

<span data-ttu-id="33be5-119">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="33be5-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="33be5-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="33be5-120">Requirements</span></span>
------------
><span data-ttu-id="33be5-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="33be5-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="33be5-122">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="33be5-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="33be5-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33be5-123">See also</span></span>


[<span data-ttu-id="33be5-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="33be5-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



