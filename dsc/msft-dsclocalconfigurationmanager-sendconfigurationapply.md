---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="53078-103">Metodo SendConfigurationApply della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="53078-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="53078-104">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="53078-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="53078-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="53078-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="53078-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="53078-106">Parameters</span></span>
----------

<span data-ttu-id="53078-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="53078-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="53078-108">I dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="53078-108">The environment data for the configuration.</span></span>

<span data-ttu-id="53078-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="53078-109">*force* \[in\]</span></span>  
<span data-ttu-id="53078-110">**true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="53078-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="53078-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="53078-111">Return value</span></span>
------------

<span data-ttu-id="53078-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="53078-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="53078-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="53078-113">Remarks</span></span>

<span data-ttu-id="53078-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="53078-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="53078-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="53078-115">Requirements</span></span>
------------
><span data-ttu-id="53078-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="53078-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="53078-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="53078-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="53078-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53078-118">See also</span></span>


[<span data-ttu-id="53078-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="53078-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



