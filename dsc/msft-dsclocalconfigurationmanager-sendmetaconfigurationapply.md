---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dea2a-103">Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="dea2a-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dea2a-104">Consente di configurare le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="dea2a-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="dea2a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dea2a-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="dea2a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="dea2a-106">Parameters</span></span>
----------

<span data-ttu-id="dea2a-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="dea2a-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="dea2a-108">I dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="dea2a-108">The environment data for the configuration.</span></span>

<span data-ttu-id="dea2a-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="dea2a-109">*force* \[in\]</span></span>  
<span data-ttu-id="dea2a-110">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="dea2a-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="dea2a-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="dea2a-111">Return value</span></span>
------------

<span data-ttu-id="dea2a-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="dea2a-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dea2a-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="dea2a-113">Remarks</span></span>

<span data-ttu-id="dea2a-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="dea2a-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dea2a-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="dea2a-115">Requirements</span></span>
------------
><span data-ttu-id="dea2a-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dea2a-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="dea2a-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dea2a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="dea2a-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dea2a-118">See also</span></span>


[<span data-ttu-id="dea2a-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dea2a-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



