---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893206"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="39214-103">Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="39214-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="39214-104">Chiama direttamente il metodo di **Get** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="39214-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="39214-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39214-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="39214-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="39214-106">Parameters</span></span>

<span data-ttu-id="39214-107">*ResourceType* \[in\] Nome della risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="39214-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="39214-108">*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.</span><span class="sxs-lookup"><span data-stu-id="39214-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="39214-109">*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore.</span><span class="sxs-lookup"><span data-stu-id="39214-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="39214-110">Usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per individuare le proprietà delle risorse e i relativi tipi.</span><span class="sxs-lookup"><span data-stu-id="39214-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="39214-111">*configurations* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="39214-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="39214-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="39214-112">Return value</span></span>

<span data-ttu-id="39214-113">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="39214-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="39214-114">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="39214-114">Remarks</span></span>

<span data-ttu-id="39214-115">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="39214-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="39214-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="39214-116">Requirements</span></span>

<span data-ttu-id="39214-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="39214-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="39214-118">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="39214-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="39214-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39214-119">See also</span></span>

[<span data-ttu-id="39214-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="39214-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)