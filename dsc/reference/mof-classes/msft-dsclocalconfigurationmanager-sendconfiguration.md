---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047548"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4af42-103">Metodo SendConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4af42-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4af42-104">Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.</span><span class="sxs-lookup"><span data-stu-id="4af42-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="4af42-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4af42-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4af42-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="4af42-106">Parameters</span></span>

<span data-ttu-id="4af42-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4af42-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="4af42-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="4af42-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4af42-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4af42-109">Return value</span></span>

<span data-ttu-id="4af42-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="4af42-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4af42-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4af42-111">Remarks</span></span>

<span data-ttu-id="4af42-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="4af42-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4af42-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4af42-113">Requirements</span></span>

<span data-ttu-id="4af42-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4af42-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4af42-115">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4af42-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4af42-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4af42-116">See also</span></span>

[<span data-ttu-id="4af42-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4af42-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)