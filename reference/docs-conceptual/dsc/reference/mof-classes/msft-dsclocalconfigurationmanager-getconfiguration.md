---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfiguration
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955048"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="c4935-103">Metodo GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4935-103">GetConfiguration method</span></span>

<span data-ttu-id="c4935-104">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c4935-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4935-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c4935-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="c4935-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="c4935-106">Parameters</span></span>

<span data-ttu-id="c4935-107">*configurationData* \[in\] Specifica i dati di configurazione da inviare.</span><span class="sxs-lookup"><span data-stu-id="c4935-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="c4935-108">*configurations* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="c4935-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="c4935-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="c4935-109">Return value</span></span>

<span data-ttu-id="c4935-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="c4935-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4935-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c4935-111">Remarks</span></span>

<span data-ttu-id="c4935-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="c4935-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4935-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c4935-113">Requirements</span></span>

<span data-ttu-id="c4935-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c4935-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c4935-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4935-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c4935-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c4935-116">See also</span></span>

[<span data-ttu-id="c4935-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c4935-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
