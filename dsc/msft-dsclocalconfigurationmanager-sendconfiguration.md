---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="36621-103">Metodo SendConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="36621-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="36621-104">Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.</span><span class="sxs-lookup"><span data-stu-id="36621-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="36621-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="36621-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="36621-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="36621-106">Parameters</span></span>
----------

<span data-ttu-id="36621-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="36621-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="36621-108">I dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="36621-108">The environment data for the configuration.</span></span>

<span data-ttu-id="36621-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="36621-109">*force* \[in\]</span></span>  
<span data-ttu-id="36621-110">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="36621-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="36621-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="36621-111">Return value</span></span>
------------

<span data-ttu-id="36621-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="36621-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36621-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="36621-113">Remarks</span></span>

<span data-ttu-id="36621-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="36621-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36621-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="36621-115">Requirements</span></span>
------------
><span data-ttu-id="36621-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="36621-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="36621-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="36621-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="36621-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="36621-118">See also</span></span>


[<span data-ttu-id="36621-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="36621-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



