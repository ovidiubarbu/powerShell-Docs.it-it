---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892400"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="22f75-103">Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="22f75-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="22f75-104">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="22f75-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="22f75-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="22f75-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="22f75-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="22f75-106">Parameters</span></span>

<span data-ttu-id="22f75-107">*BreakAll* \[in\] Imposta un punto di interruzione su ogni riga nello script della risorsa.</span><span class="sxs-lookup"><span data-stu-id="22f75-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="22f75-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="22f75-108">Return value</span></span>

<span data-ttu-id="22f75-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="22f75-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="22f75-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="22f75-110">Remarks</span></span>

<span data-ttu-id="22f75-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="22f75-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="22f75-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="22f75-112">Requirements</span></span>

<span data-ttu-id="22f75-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="22f75-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="22f75-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="22f75-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="22f75-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="22f75-115">See also</span></span>

[<span data-ttu-id="22f75-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="22f75-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)