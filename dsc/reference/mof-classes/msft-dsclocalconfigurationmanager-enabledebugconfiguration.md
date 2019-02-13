---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678009"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="77cb8-103">Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="77cb8-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="77cb8-104">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="77cb8-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="77cb8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="77cb8-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="77cb8-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="77cb8-106">Parameters</span></span>

<span data-ttu-id="77cb8-107">*BreakAll* \[in\] Imposta un punto di interruzione su ogni riga nello script della risorsa.</span><span class="sxs-lookup"><span data-stu-id="77cb8-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="77cb8-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="77cb8-108">Return value</span></span>

<span data-ttu-id="77cb8-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="77cb8-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="77cb8-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="77cb8-110">Remarks</span></span>

<span data-ttu-id="77cb8-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="77cb8-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="77cb8-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="77cb8-112">Requirements</span></span>

<span data-ttu-id="77cb8-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="77cb8-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="77cb8-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="77cb8-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="77cb8-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="77cb8-115">See also</span></span>

[<span data-ttu-id="77cb8-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="77cb8-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)