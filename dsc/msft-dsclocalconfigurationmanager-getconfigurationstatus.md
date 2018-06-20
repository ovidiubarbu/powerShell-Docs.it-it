---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221766"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bd274-103">Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bd274-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bd274-104">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="bd274-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="bd274-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bd274-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="bd274-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="bd274-106">Parameters</span></span>
----------

<span data-ttu-id="bd274-107">*All* \[in\] **true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione nel computer, compresa l'applicazione di configurazione e la verifica di coerenza.</span><span class="sxs-lookup"><span data-stu-id="bd274-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="bd274-108">*configurationStatus* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="bd274-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd274-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="bd274-109">Return value</span></span>
------------

<span data-ttu-id="bd274-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="bd274-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd274-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="bd274-111">Remarks</span></span>

<span data-ttu-id="bd274-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="bd274-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd274-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bd274-113">Requirements</span></span>
------------
><span data-ttu-id="bd274-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bd274-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bd274-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd274-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bd274-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bd274-116">See also</span></span>


[<span data-ttu-id="bd274-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bd274-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)