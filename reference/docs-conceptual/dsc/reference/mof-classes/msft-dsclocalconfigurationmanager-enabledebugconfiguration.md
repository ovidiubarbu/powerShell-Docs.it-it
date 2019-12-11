---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953438"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="3a800-103">Metodo EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="3a800-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="3a800-104">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="3a800-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a800-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3a800-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="3a800-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="3a800-106">Parameters</span></span>

<span data-ttu-id="3a800-107">*BreakAll* \[in\] Imposta un punto di interruzione su ogni riga nello script della risorsa.</span><span class="sxs-lookup"><span data-stu-id="3a800-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="3a800-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3a800-108">Return value</span></span>

<span data-ttu-id="3a800-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="3a800-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a800-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3a800-110">Remarks</span></span>

<span data-ttu-id="3a800-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="3a800-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a800-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3a800-112">Requirements</span></span>

<span data-ttu-id="3a800-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3a800-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3a800-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3a800-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3a800-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3a800-115">See also</span></span>

[<span data-ttu-id="3a800-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3a800-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
