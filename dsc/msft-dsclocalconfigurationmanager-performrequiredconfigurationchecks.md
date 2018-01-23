---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="74007-103">Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="74007-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="74007-104">Avvia una verifica di coerenza usando l'Utilità di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="74007-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="74007-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="74007-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="74007-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="74007-106">Parameters</span></span>
----------

<span data-ttu-id="74007-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="74007-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="74007-108">Una maschera di bit che specifica il tipo di verifica di coerenza da eseguire.</span><span class="sxs-lookup"><span data-stu-id="74007-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="74007-109">I valori seguenti sono validi e possono essere combinati tramite un'operazione bit per bit **OR**:</span><span class="sxs-lookup"><span data-stu-id="74007-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="74007-110">Value</span><span class="sxs-lookup"><span data-stu-id="74007-110">Value</span></span> |<span data-ttu-id="74007-111">Description</span><span class="sxs-lookup"><span data-stu-id="74007-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="74007-112">**1**</span><span class="sxs-lookup"><span data-stu-id="74007-112">**1**</span></span> | <span data-ttu-id="74007-113">Una verifica di coerenza normale.</span><span class="sxs-lookup"><span data-stu-id="74007-113">A normal consistency check.</span></span> |
|<span data-ttu-id="74007-114">**2**</span><span class="sxs-lookup"><span data-stu-id="74007-114">**2**</span></span> | <span data-ttu-id="74007-115">La continuazione di una verifica di coerenza dopo un riavvio.</span><span class="sxs-lookup"><span data-stu-id="74007-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="74007-116">Questo valore non deve essere combinato con altri valori.</span><span class="sxs-lookup"><span data-stu-id="74007-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="74007-117">**4**</span><span class="sxs-lookup"><span data-stu-id="74007-117">**4**</span></span> | <span data-ttu-id="74007-118">La configurazione deve essere recuperata dal server di pull specificato nella metaconfigurazione per il nodo.</span><span class="sxs-lookup"><span data-stu-id="74007-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="74007-119">Questo valore deve essere sempre combinato con **1** per un valore di **5**.</span><span class="sxs-lookup"><span data-stu-id="74007-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="74007-120">**8**</span><span class="sxs-lookup"><span data-stu-id="74007-120">**8**</span></span> | <span data-ttu-id="74007-121">Inviare lo stato al server di report.</span><span class="sxs-lookup"><span data-stu-id="74007-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="74007-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="74007-122">Return value</span></span>
------------

<span data-ttu-id="74007-123">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="74007-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="74007-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="74007-124">Remarks</span></span>

<span data-ttu-id="74007-125">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="74007-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="74007-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="74007-126">Requirements</span></span>
------------
><span data-ttu-id="74007-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="74007-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="74007-128">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="74007-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="74007-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="74007-129">See also</span></span>


[<span data-ttu-id="74007-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="74007-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



