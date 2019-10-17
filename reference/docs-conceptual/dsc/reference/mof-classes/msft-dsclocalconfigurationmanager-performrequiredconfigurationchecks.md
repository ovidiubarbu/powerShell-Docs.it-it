---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo PerformRequiredConfigurationChecks
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955008"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="18860-103">Metodo PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="18860-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="18860-104">Avvia una verifica di coerenza usando l'Utilità di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="18860-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="18860-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="18860-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="18860-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="18860-106">Parameters</span></span>

<span data-ttu-id="18860-107">*Flags* \[in\] Maschera di bit che specifica il tipo di verifica di coerenza da eseguire.</span><span class="sxs-lookup"><span data-stu-id="18860-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="18860-108">I valori seguenti sono validi e possono essere combinati tramite un'operazione bit per bit **OR**:</span><span class="sxs-lookup"><span data-stu-id="18860-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="18860-109">Value</span><span class="sxs-lookup"><span data-stu-id="18860-109">Value</span></span> |<span data-ttu-id="18860-110">Description</span><span class="sxs-lookup"><span data-stu-id="18860-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="18860-111">**1**</span><span class="sxs-lookup"><span data-stu-id="18860-111">**1**</span></span> | <span data-ttu-id="18860-112">Una verifica di coerenza normale.</span><span class="sxs-lookup"><span data-stu-id="18860-112">A normal consistency check.</span></span> |
|<span data-ttu-id="18860-113">**2**</span><span class="sxs-lookup"><span data-stu-id="18860-113">**2**</span></span> | <span data-ttu-id="18860-114">La continuazione di una verifica di coerenza dopo un riavvio.</span><span class="sxs-lookup"><span data-stu-id="18860-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="18860-115">Questo valore non deve essere combinato con altri valori.</span><span class="sxs-lookup"><span data-stu-id="18860-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="18860-116">**4**</span><span class="sxs-lookup"><span data-stu-id="18860-116">**4**</span></span> | <span data-ttu-id="18860-117">La configurazione deve essere recuperata dal server di pull specificato nella metaconfigurazione per il nodo.</span><span class="sxs-lookup"><span data-stu-id="18860-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="18860-118">Questo valore deve essere sempre combinato con **1** per un valore di **5**.</span><span class="sxs-lookup"><span data-stu-id="18860-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="18860-119">**8**</span><span class="sxs-lookup"><span data-stu-id="18860-119">**8**</span></span> | <span data-ttu-id="18860-120">Inviare lo stato al server di report.</span><span class="sxs-lookup"><span data-stu-id="18860-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="18860-121">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="18860-121">Return value</span></span>

<span data-ttu-id="18860-122">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="18860-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18860-123">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="18860-123">Remarks</span></span>

<span data-ttu-id="18860-124">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="18860-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18860-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="18860-125">Requirements</span></span>

<span data-ttu-id="18860-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18860-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="18860-127">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18860-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="18860-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="18860-128">See also</span></span>

[<span data-ttu-id="18860-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18860-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)