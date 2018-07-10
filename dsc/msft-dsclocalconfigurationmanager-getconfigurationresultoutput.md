---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893944"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d0b3a-103">Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d0b3a-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d0b3a-104">Recupera l'output dell'agente di configurazione associato a un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="d0b3a-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0b3a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d0b3a-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="d0b3a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="d0b3a-106">Parameters</span></span>

<span data-ttu-id="d0b3a-107">*jobId* \[in\] ID del processo per cui ottenere i dati di output.</span><span class="sxs-lookup"><span data-stu-id="d0b3a-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="d0b3a-108">*resumeOutputBookmark* \[in\] Specifica che l'output deve essere la continuazione di un segnalibro precedente.</span><span class="sxs-lookup"><span data-stu-id="d0b3a-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="d0b3a-109">*output* \[out\] Output per il processo specificato.</span><span class="sxs-lookup"><span data-stu-id="d0b3a-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0b3a-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d0b3a-110">Return value</span></span>

<span data-ttu-id="d0b3a-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="d0b3a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0b3a-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d0b3a-112">Remarks</span></span>

<span data-ttu-id="d0b3a-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="d0b3a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0b3a-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d0b3a-114">Requirements</span></span>

<span data-ttu-id="d0b3a-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d0b3a-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d0b3a-116">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0b3a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d0b3a-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d0b3a-117">See also</span></span>

[<span data-ttu-id="d0b3a-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d0b3a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)