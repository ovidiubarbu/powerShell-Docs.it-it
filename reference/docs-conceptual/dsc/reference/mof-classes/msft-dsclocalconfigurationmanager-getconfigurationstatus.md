---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71955018"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="6cdea-103">Metodo GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="6cdea-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="6cdea-104">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="6cdea-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="6cdea-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6cdea-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="6cdea-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="6cdea-106">Parameters</span></span>

<span data-ttu-id="6cdea-107">*All* \[in\] **true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione sulla macchina, compresa l'applicazione di configurazione e la verifica coerenza.</span><span class="sxs-lookup"><span data-stu-id="6cdea-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="6cdea-108">*configurationStatus* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="6cdea-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="6cdea-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="6cdea-109">Return value</span></span>

<span data-ttu-id="6cdea-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="6cdea-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cdea-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="6cdea-111">Remarks</span></span>

<span data-ttu-id="6cdea-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="6cdea-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6cdea-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6cdea-113">Requirements</span></span>

<span data-ttu-id="6cdea-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6cdea-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6cdea-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6cdea-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6cdea-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6cdea-116">See also</span></span>

[<span data-ttu-id="6cdea-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6cdea-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
