---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681422"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e736a-103">Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e736a-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e736a-104">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="e736a-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="e736a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e736a-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="e736a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="e736a-106">Parameters</span></span>

<span data-ttu-id="e736a-107">*All* \[in\] **true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione nel computer, compresa l'applicazione di configurazione e la verifica di coerenza.</span><span class="sxs-lookup"><span data-stu-id="e736a-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="e736a-108">*configurationStatus* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="e736a-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="e736a-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e736a-109">Return value</span></span>

<span data-ttu-id="e736a-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="e736a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e736a-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="e736a-111">Remarks</span></span>

<span data-ttu-id="e736a-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="e736a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e736a-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e736a-113">Requirements</span></span>

<span data-ttu-id="e736a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e736a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e736a-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e736a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e736a-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e736a-116">See also</span></span>

[<span data-ttu-id="e736a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e736a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)