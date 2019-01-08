---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047507"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2cee5-103">Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2cee5-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2cee5-104">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="2cee5-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="2cee5-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2cee5-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2cee5-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="2cee5-106">Parameters</span></span>

<span data-ttu-id="2cee5-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="2cee5-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="2cee5-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="2cee5-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2cee5-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2cee5-109">Return value</span></span>

<span data-ttu-id="2cee5-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="2cee5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cee5-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2cee5-111">Remarks</span></span>

<span data-ttu-id="2cee5-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="2cee5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2cee5-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2cee5-113">Requirements</span></span>

<span data-ttu-id="2cee5-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2cee5-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2cee5-115">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cee5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2cee5-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2cee5-116">See also</span></span>

[<span data-ttu-id="2cee5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2cee5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)