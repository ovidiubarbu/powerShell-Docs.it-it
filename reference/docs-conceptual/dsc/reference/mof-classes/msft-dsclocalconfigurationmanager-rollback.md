---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954938"
---
# <a name="rollback-method"></a><span data-ttu-id="08fd8-103">Metodo RollBack</span><span class="sxs-lookup"><span data-stu-id="08fd8-103">RollBack method</span></span>

<span data-ttu-id="08fd8-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="08fd8-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="08fd8-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="08fd8-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="08fd8-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="08fd8-106">Parameters</span></span>

<span data-ttu-id="08fd8-107">*configurationNumber* \[in\] Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="08fd8-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="08fd8-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="08fd8-108">Return value</span></span>

<span data-ttu-id="08fd8-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="08fd8-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="08fd8-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="08fd8-110">Remarks</span></span>

<span data-ttu-id="08fd8-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="08fd8-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="08fd8-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="08fd8-112">Requirements</span></span>

<span data-ttu-id="08fd8-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="08fd8-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="08fd8-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="08fd8-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="08fd8-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="08fd8-115">See also</span></span>

[<span data-ttu-id="08fd8-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="08fd8-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
