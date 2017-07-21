---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7fde1-103">Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7fde1-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7fde1-104">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="7fde1-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="7fde1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7fde1-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="7fde1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="7fde1-106">Parameters</span></span>
----------

<span data-ttu-id="7fde1-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7fde1-107">*All* \[in\]</span></span>  
<span data-ttu-id="7fde1-108">**true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione sulla macchina, compresa l'applicazione di configurazione e la verifica coerenza.</span><span class="sxs-lookup"><span data-stu-id="7fde1-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="7fde1-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="7fde1-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="7fde1-110">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="7fde1-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="7fde1-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="7fde1-111">Return value</span></span>
------------

<span data-ttu-id="7fde1-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="7fde1-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7fde1-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="7fde1-113">Remarks</span></span>

<span data-ttu-id="7fde1-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="7fde1-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7fde1-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7fde1-115">Requirements</span></span>
------------
><span data-ttu-id="7fde1-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7fde1-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7fde1-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7fde1-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7fde1-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7fde1-118">See also</span></span>


[<span data-ttu-id="7fde1-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7fde1-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



