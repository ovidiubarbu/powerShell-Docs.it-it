---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047576"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2b289-103">Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2b289-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2b289-104">Recupera l'output dell'agente di configurazione associato a un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="2b289-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b289-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2b289-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="2b289-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="2b289-106">Parameters</span></span>

<span data-ttu-id="2b289-107">*jobId* \[in\] ID del processo per cui ottenere i dati di output.</span><span class="sxs-lookup"><span data-stu-id="2b289-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="2b289-108">*resumeOutputBookmark* \[in\] Specifica che l'output deve essere la continuazione di un segnalibro precedente.</span><span class="sxs-lookup"><span data-stu-id="2b289-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="2b289-109">*output* \[out\] Output per il processo specificato.</span><span class="sxs-lookup"><span data-stu-id="2b289-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b289-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2b289-110">Return value</span></span>

<span data-ttu-id="2b289-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="2b289-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b289-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="2b289-112">Remarks</span></span>

<span data-ttu-id="2b289-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="2b289-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b289-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2b289-114">Requirements</span></span>

<span data-ttu-id="2b289-115">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2b289-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2b289-116">spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b289-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2b289-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2b289-117">See also</span></span>

[<span data-ttu-id="2b289-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2b289-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)