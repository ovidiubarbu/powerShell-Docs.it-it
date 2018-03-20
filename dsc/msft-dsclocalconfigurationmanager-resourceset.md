---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3486ef559102929f8d05994a4bf6e45d49a0c140
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="aae1c-103">Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="aae1c-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="aae1c-104">Chiama direttamente il metodo di **Set** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="aae1c-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="aae1c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aae1c-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="aae1c-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="aae1c-106">Parameters</span></span>
----------

<span data-ttu-id="aae1c-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="aae1c-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="aae1c-108">Il nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="aae1c-108">The name of the resource to call.</span></span>

<span data-ttu-id="aae1c-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="aae1c-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="aae1c-110">Il nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="aae1c-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="aae1c-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="aae1c-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="aae1c-112">Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="aae1c-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="aae1c-113">Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="aae1c-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="aae1c-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="aae1c-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="aae1c-115">In fase di restituzione, questa proprietà è impostata su **true** se il nodo deve essere riavviato.</span><span class="sxs-lookup"><span data-stu-id="aae1c-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="aae1c-116">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="aae1c-116">Return value</span></span>
------------

<span data-ttu-id="aae1c-117">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="aae1c-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aae1c-118">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="aae1c-118">Remarks</span></span>

<span data-ttu-id="aae1c-119">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="aae1c-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aae1c-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aae1c-120">Requirements</span></span>
------------
><span data-ttu-id="aae1c-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aae1c-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="aae1c-122">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aae1c-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="aae1c-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aae1c-123">See also</span></span>


[<span data-ttu-id="aae1c-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aae1c-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



