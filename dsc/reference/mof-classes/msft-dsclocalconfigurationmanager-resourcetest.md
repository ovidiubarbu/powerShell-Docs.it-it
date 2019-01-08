---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047687"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a48e0-103">Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a48e0-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a48e0-104">Chiama direttamente il metodo di **Test** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="a48e0-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="a48e0-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a48e0-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="a48e0-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="a48e0-106">Parameters</span></span>

<span data-ttu-id="a48e0-107">*ResourceType* \[in\] Nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="a48e0-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="a48e0-108">*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="a48e0-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="a48e0-109">*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="a48e0-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="a48e0-110">Usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="a48e0-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="a48e0-111">*InDesiredState* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo di destinazione è nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="a48e0-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="a48e0-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="a48e0-112">Return value</span></span>

<span data-ttu-id="a48e0-113">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="a48e0-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a48e0-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="a48e0-114">Remarks</span></span>

<span data-ttu-id="a48e0-115">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="a48e0-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a48e0-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a48e0-116">Requirements</span></span>

<span data-ttu-id="a48e0-117">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a48e0-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a48e0-118">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a48e0-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a48e0-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a48e0-119">See also</span></span>

[<span data-ttu-id="a48e0-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a48e0-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)