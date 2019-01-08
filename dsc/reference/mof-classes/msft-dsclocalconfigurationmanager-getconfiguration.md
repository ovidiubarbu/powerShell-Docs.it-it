---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047879"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="21fc0-103">Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="21fc0-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="21fc0-104">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="21fc0-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="21fc0-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="21fc0-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="21fc0-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="21fc0-106">Parameters</span></span>

<span data-ttu-id="21fc0-107">*configurationData* \[in\] Specifica i dati di configurazione da inviare.</span><span class="sxs-lookup"><span data-stu-id="21fc0-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="21fc0-108">*configurations* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="21fc0-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="21fc0-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="21fc0-109">Return value</span></span>

<span data-ttu-id="21fc0-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="21fc0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="21fc0-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="21fc0-111">Remarks</span></span>

<span data-ttu-id="21fc0-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="21fc0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="21fc0-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="21fc0-113">Requirements</span></span>

<span data-ttu-id="21fc0-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="21fc0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="21fc0-115">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="21fc0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="21fc0-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="21fc0-116">See also</span></span>

[<span data-ttu-id="21fc0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="21fc0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)