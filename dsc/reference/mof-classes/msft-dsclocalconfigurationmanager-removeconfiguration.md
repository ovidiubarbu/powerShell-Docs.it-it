---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734392"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="3da82-103">Metodo RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="3da82-103">RemoveConfiguration method</span></span>

<span data-ttu-id="3da82-104">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="3da82-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="3da82-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3da82-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="3da82-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="3da82-106">Parameters</span></span>

<span data-ttu-id="3da82-107">*Stage* \[in\] Specifica il documento di configurazione da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="3da82-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="3da82-108">I valori validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="3da82-108">The following values are valid:</span></span>

|<span data-ttu-id="3da82-109">Value</span><span class="sxs-lookup"><span data-stu-id="3da82-109">Value</span></span> |<span data-ttu-id="3da82-110">Description</span><span class="sxs-lookup"><span data-stu-id="3da82-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="3da82-111">**1**</span><span class="sxs-lookup"><span data-stu-id="3da82-111">**1**</span></span> | <span data-ttu-id="3da82-112">Il documento di configurazione **corrente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="3da82-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="3da82-113">**2**</span><span class="sxs-lookup"><span data-stu-id="3da82-113">**2**</span></span> | <span data-ttu-id="3da82-114">Il documento di configurazione **in sospeso** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="3da82-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="3da82-115">**4**</span><span class="sxs-lookup"><span data-stu-id="3da82-115">**4**</span></span> | <span data-ttu-id="3da82-116">Il documento di configurazione **precedente** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="3da82-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="3da82-117">*Force* \[in\] **true** per forzare la rimozione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="3da82-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3da82-118">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3da82-118">Return value</span></span>

<span data-ttu-id="3da82-119">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="3da82-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3da82-120">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="3da82-120">Remarks</span></span>

<span data-ttu-id="3da82-121">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="3da82-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3da82-122">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3da82-122">Requirements</span></span>

<span data-ttu-id="3da82-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3da82-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3da82-124">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3da82-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3da82-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3da82-125">See also</span></span>

[<span data-ttu-id="3da82-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3da82-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
