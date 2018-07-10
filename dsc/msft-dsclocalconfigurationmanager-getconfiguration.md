---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892543"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="91054-103">Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="91054-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="91054-104">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="91054-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="91054-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="91054-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="91054-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="91054-106">Parameters</span></span>

<span data-ttu-id="91054-107">*configurationData* \[in\] Specifica i dati di configurazione da inviare.</span><span class="sxs-lookup"><span data-stu-id="91054-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="91054-108">*configurations* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="91054-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="91054-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="91054-109">Return value</span></span>

<span data-ttu-id="91054-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="91054-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="91054-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="91054-111">Remarks</span></span>

<span data-ttu-id="91054-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="91054-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="91054-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="91054-113">Requirements</span></span>

<span data-ttu-id="91054-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="91054-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="91054-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="91054-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="91054-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="91054-116">See also</span></span>

[<span data-ttu-id="91054-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="91054-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)