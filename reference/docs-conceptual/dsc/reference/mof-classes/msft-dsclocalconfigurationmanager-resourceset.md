---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954958"
---
# <a name="resourceset-method"></a><span data-ttu-id="75733-103">Metodo ResourceSet</span><span class="sxs-lookup"><span data-stu-id="75733-103">ResourceSet method</span></span>

<span data-ttu-id="75733-104">Chiama direttamente il metodo di **Set** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="75733-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="75733-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="75733-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="75733-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="75733-106">Parameters</span></span>

<span data-ttu-id="75733-107">*ResourceType* \[in\] Nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="75733-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="75733-108">*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="75733-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="75733-109">*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="75733-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="75733-110">Usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="75733-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="75733-111">*RebootRequired* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo deve essere riavviato.</span><span class="sxs-lookup"><span data-stu-id="75733-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="75733-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="75733-112">Return value</span></span>

<span data-ttu-id="75733-113">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="75733-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="75733-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="75733-114">Remarks</span></span>

<span data-ttu-id="75733-115">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="75733-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="75733-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="75733-116">Requirements</span></span>

<span data-ttu-id="75733-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="75733-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="75733-118">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="75733-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="75733-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="75733-119">See also</span></span>

[<span data-ttu-id="75733-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="75733-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
