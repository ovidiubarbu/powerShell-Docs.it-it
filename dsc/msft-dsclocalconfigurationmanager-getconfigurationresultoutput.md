---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9a1f9-103">Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9a1f9-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9a1f9-104">Recupera l'output dell'agente di configurazione associato a un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="9a1f9-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9a1f9-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="9a1f9-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9a1f9-106">Parameters</span></span>
----------

<span data-ttu-id="9a1f9-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9a1f9-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="9a1f9-108">L'ID del processo di cui ottenere i dati di output.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="9a1f9-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9a1f9-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="9a1f9-110">Specifica che l'output deve essere la continuazione di un segnalibro precedente.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="9a1f9-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9a1f9-111">*output* \[out\]</span></span>  
<span data-ttu-id="9a1f9-112">L'output per il processo specificato.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="9a1f9-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9a1f9-113">Return value</span></span>
------------

<span data-ttu-id="9a1f9-114">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a1f9-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9a1f9-115">Remarks</span></span>

<span data-ttu-id="9a1f9-116">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a1f9-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9a1f9-117">Requirements</span></span>
------------
><span data-ttu-id="9a1f9-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9a1f9-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9a1f9-119">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9a1f9-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9a1f9-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a1f9-120">See also</span></span>


[<span data-ttu-id="9a1f9-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9a1f9-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



