---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b4c70-103">Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b4c70-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b4c70-104">Recupera l'output dell'agente di configurazione associato a un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="b4c70-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="b4c70-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b4c70-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="b4c70-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="b4c70-106">Parameters</span></span>
----------

<span data-ttu-id="b4c70-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b4c70-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="b4c70-108">L'ID del processo di cui ottenere i dati di output.</span><span class="sxs-lookup"><span data-stu-id="b4c70-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b4c70-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b4c70-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="b4c70-110">Specifica che l'output deve essere la continuazione di un segnalibro precedente.</span><span class="sxs-lookup"><span data-stu-id="b4c70-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b4c70-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b4c70-111">*output* \[out\]</span></span>  
<span data-ttu-id="b4c70-112">L'output per il processo specificato.</span><span class="sxs-lookup"><span data-stu-id="b4c70-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b4c70-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b4c70-113">Return value</span></span>
------------

<span data-ttu-id="b4c70-114">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="b4c70-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4c70-115">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="b4c70-115">Remarks</span></span>

<span data-ttu-id="b4c70-116">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="b4c70-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4c70-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b4c70-117">Requirements</span></span>
------------
><span data-ttu-id="b4c70-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b4c70-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b4c70-119">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4c70-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b4c70-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b4c70-120">See also</span></span>


[<span data-ttu-id="b4c70-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b4c70-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



