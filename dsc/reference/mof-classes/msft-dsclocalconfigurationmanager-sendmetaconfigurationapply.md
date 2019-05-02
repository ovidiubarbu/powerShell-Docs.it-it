---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078313"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="44835-103">Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="44835-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="44835-104">Consente di configurare le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="44835-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="44835-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="44835-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="44835-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="44835-106">Parameters</span></span>

<span data-ttu-id="44835-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="44835-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="44835-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="44835-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="44835-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="44835-109">Return value</span></span>

<span data-ttu-id="44835-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="44835-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="44835-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="44835-111">Remarks</span></span>

<span data-ttu-id="44835-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="44835-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="44835-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="44835-113">Requirements</span></span>

<span data-ttu-id="44835-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="44835-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="44835-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="44835-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="44835-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="44835-116">See also</span></span>

[<span data-ttu-id="44835-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="44835-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)