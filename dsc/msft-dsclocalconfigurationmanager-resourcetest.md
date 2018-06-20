---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 714bbb286ebbe4ed0f1faa15e03ac4b51a3ee87f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218859"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bd484-103">Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bd484-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bd484-104">Chiama direttamente il metodo di **Test** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="bd484-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="bd484-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bd484-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="bd484-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="bd484-106">Parameters</span></span>
----------

<span data-ttu-id="bd484-107">*ResourceType* \[in\] Nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="bd484-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="bd484-108">*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="bd484-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="bd484-109">*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="bd484-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="bd484-110">Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="bd484-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="bd484-111">*InDesiredState* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo di destinazione è nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="bd484-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd484-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="bd484-112">Return value</span></span>
------------

<span data-ttu-id="bd484-113">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="bd484-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd484-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bd484-114">Remarks</span></span>

<span data-ttu-id="bd484-115">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="bd484-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd484-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bd484-116">Requirements</span></span>
------------
><span data-ttu-id="bd484-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bd484-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bd484-118">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd484-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bd484-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bd484-119">See also</span></span>


[<span data-ttu-id="bd484-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bd484-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)