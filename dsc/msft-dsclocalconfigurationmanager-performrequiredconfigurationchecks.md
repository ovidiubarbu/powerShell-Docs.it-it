---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e7d46-103">Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e7d46-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e7d46-104">Avvia una verifica di coerenza usando l'Utilità di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="e7d46-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="e7d46-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e7d46-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="e7d46-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="e7d46-106">Parameters</span></span>
----------

<span data-ttu-id="e7d46-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e7d46-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="e7d46-108">Una maschera di bit che specifica il tipo di verifica di coerenza da eseguire.</span><span class="sxs-lookup"><span data-stu-id="e7d46-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="e7d46-109">I valori seguenti sono validi e possono essere combinati tramite un'operazione bit per bit **OR**:</span><span class="sxs-lookup"><span data-stu-id="e7d46-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="e7d46-110">Valore</span><span class="sxs-lookup"><span data-stu-id="e7d46-110">Value</span></span> |<span data-ttu-id="e7d46-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e7d46-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e7d46-112">**1**</span><span class="sxs-lookup"><span data-stu-id="e7d46-112">**1**</span></span> | <span data-ttu-id="e7d46-113">Una verifica di coerenza normale.</span><span class="sxs-lookup"><span data-stu-id="e7d46-113">A normal consistency check.</span></span> |
|<span data-ttu-id="e7d46-114">**2**</span><span class="sxs-lookup"><span data-stu-id="e7d46-114">**2**</span></span> | <span data-ttu-id="e7d46-115">La continuazione di una verifica di coerenza dopo un riavvio.</span><span class="sxs-lookup"><span data-stu-id="e7d46-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="e7d46-116">Questo valore non deve essere combinato con altri valori.</span><span class="sxs-lookup"><span data-stu-id="e7d46-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="e7d46-117">**4**</span><span class="sxs-lookup"><span data-stu-id="e7d46-117">**4**</span></span> | <span data-ttu-id="e7d46-118">La configurazione deve essere recuperata dal server di pull specificato nella metaconfigurazione per il nodo.</span><span class="sxs-lookup"><span data-stu-id="e7d46-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="e7d46-119">Questo valore deve essere sempre combinato con **1** per un valore di **5**.</span><span class="sxs-lookup"><span data-stu-id="e7d46-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="e7d46-120">**8**</span><span class="sxs-lookup"><span data-stu-id="e7d46-120">**8**</span></span> | <span data-ttu-id="e7d46-121">Inviare lo stato al server di report.</span><span class="sxs-lookup"><span data-stu-id="e7d46-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e7d46-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e7d46-122">Return value</span></span>
------------

<span data-ttu-id="e7d46-123">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="e7d46-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7d46-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e7d46-124">Remarks</span></span>

<span data-ttu-id="e7d46-125">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="e7d46-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7d46-126">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e7d46-126">Requirements</span></span>
------------
><span data-ttu-id="e7d46-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e7d46-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e7d46-128">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7d46-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e7d46-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7d46-129">See also</span></span>


[<span data-ttu-id="e7d46-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e7d46-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



