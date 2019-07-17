---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727032"
---
# <a name="rollback-method"></a><span data-ttu-id="ccf53-103">Metodo RollBack</span><span class="sxs-lookup"><span data-stu-id="ccf53-103">RollBack method</span></span>

<span data-ttu-id="ccf53-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="ccf53-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="ccf53-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ccf53-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="ccf53-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="ccf53-106">Parameters</span></span>

<span data-ttu-id="ccf53-107">*configurationNumber* \[in\] Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="ccf53-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ccf53-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ccf53-108">Return value</span></span>

<span data-ttu-id="ccf53-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="ccf53-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccf53-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ccf53-110">Remarks</span></span>

<span data-ttu-id="ccf53-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="ccf53-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ccf53-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ccf53-112">Requirements</span></span>

<span data-ttu-id="ccf53-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ccf53-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ccf53-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ccf53-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ccf53-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ccf53-115">See also</span></span>

[<span data-ttu-id="ccf53-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ccf53-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
