---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893876"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9127c-103">Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9127c-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9127c-104">Arresta la modifica della configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="9127c-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="9127c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9127c-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9127c-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9127c-106">Parameters</span></span>

<span data-ttu-id="9127c-107">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="9127c-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9127c-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9127c-108">Return value</span></span>

<span data-ttu-id="9127c-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="9127c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9127c-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9127c-110">Remarks</span></span>

<span data-ttu-id="9127c-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="9127c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9127c-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9127c-112">Requirements</span></span>

<span data-ttu-id="9127c-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9127c-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9127c-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9127c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9127c-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9127c-115">See also</span></span>

[<span data-ttu-id="9127c-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9127c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)