---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="89bfe-103">Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="89bfe-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="89bfe-104">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="89bfe-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="89bfe-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="89bfe-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="89bfe-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="89bfe-106">Parameters</span></span>
----------

<span data-ttu-id="89bfe-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="89bfe-107">*All* \[in\]</span></span>  
<span data-ttu-id="89bfe-108">**true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione sulla macchina, compresa l'applicazione di configurazione e la verifica coerenza.</span><span class="sxs-lookup"><span data-stu-id="89bfe-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="89bfe-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="89bfe-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="89bfe-110">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="89bfe-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="89bfe-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="89bfe-111">Return value</span></span>
------------

<span data-ttu-id="89bfe-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="89bfe-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="89bfe-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="89bfe-113">Remarks</span></span>

<span data-ttu-id="89bfe-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="89bfe-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="89bfe-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="89bfe-115">Requirements</span></span>
------------
><span data-ttu-id="89bfe-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="89bfe-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="89bfe-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="89bfe-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="89bfe-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89bfe-118">See also</span></span>


[<span data-ttu-id="89bfe-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="89bfe-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



