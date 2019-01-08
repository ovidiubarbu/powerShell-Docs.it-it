---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047735"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c47d1-103">Metodo RollBack della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c47d1-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c47d1-104">Esegue il rollback della configurazione a una versione precedente.</span><span class="sxs-lookup"><span data-stu-id="c47d1-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="c47d1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c47d1-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="c47d1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="c47d1-106">Parameters</span></span>

<span data-ttu-id="c47d1-107">*configurationNumber* \[in\] Specifica la configurazione richiesta.</span><span class="sxs-lookup"><span data-stu-id="c47d1-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c47d1-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c47d1-108">Return value</span></span>

<span data-ttu-id="c47d1-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="c47d1-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c47d1-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c47d1-110">Remarks</span></span>

<span data-ttu-id="c47d1-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="c47d1-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c47d1-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c47d1-112">Requirements</span></span>

<span data-ttu-id="c47d1-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c47d1-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c47d1-114">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c47d1-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c47d1-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c47d1-115">See also</span></span>

[<span data-ttu-id="c47d1-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c47d1-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)