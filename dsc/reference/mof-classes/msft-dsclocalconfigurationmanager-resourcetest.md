---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceTest
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727085"
---
# <a name="resourcetest-method"></a><span data-ttu-id="80916-103">Metodo ResourceTest</span><span class="sxs-lookup"><span data-stu-id="80916-103">ResourceTest method</span></span>

<span data-ttu-id="80916-104">Chiama direttamente il metodo di **Test** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="80916-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="80916-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="80916-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="80916-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="80916-106">Parameters</span></span>

<span data-ttu-id="80916-107">*ResourceType* \[in\] Nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="80916-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="80916-108">*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="80916-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="80916-109">*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="80916-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="80916-110">Usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="80916-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="80916-111">*InDesiredState* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo di destinazione è nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="80916-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="80916-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="80916-112">Return value</span></span>

<span data-ttu-id="80916-113">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="80916-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="80916-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="80916-114">Remarks</span></span>

<span data-ttu-id="80916-115">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="80916-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="80916-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="80916-116">Requirements</span></span>

<span data-ttu-id="80916-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="80916-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="80916-118">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="80916-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="80916-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="80916-119">See also</span></span>

[<span data-ttu-id="80916-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="80916-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
