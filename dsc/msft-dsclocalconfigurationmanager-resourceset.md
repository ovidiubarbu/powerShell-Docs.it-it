---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 0c9c1d33117067d76d61036d5839f0b676eb4a97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f5053-103">Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f5053-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f5053-104">Chiama direttamente il metodo di **Set** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="f5053-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="f5053-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f5053-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="f5053-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="f5053-106">Parameters</span></span>
----------

<span data-ttu-id="f5053-107">*ResourceType* \[in\] Nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="f5053-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f5053-108">*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="f5053-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f5053-109">*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="f5053-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f5053-110">Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="f5053-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f5053-111">*RebootRequired* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo deve essere riavviato.</span><span class="sxs-lookup"><span data-stu-id="f5053-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5053-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f5053-112">Return value</span></span>
------------

<span data-ttu-id="f5053-113">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="f5053-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5053-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f5053-114">Remarks</span></span>

<span data-ttu-id="f5053-115">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="f5053-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5053-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f5053-116">Requirements</span></span>
------------
><span data-ttu-id="f5053-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f5053-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f5053-118">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f5053-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f5053-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f5053-119">See also</span></span>


[<span data-ttu-id="f5053-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f5053-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)