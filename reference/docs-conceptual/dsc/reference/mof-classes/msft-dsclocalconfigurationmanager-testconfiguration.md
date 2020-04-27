---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo TestConfiguration
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954868"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="175e1-103">Metodo TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="175e1-103">TestConfiguration method</span></span>

<span data-ttu-id="175e1-104">Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.</span><span class="sxs-lookup"><span data-stu-id="175e1-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="175e1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="175e1-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="175e1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="175e1-106">Parameters</span></span>

<span data-ttu-id="175e1-107">*configurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="175e1-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="175e1-108">*InDesiredState* \[out\] Al termine dell'esecuzione, specifica se il nodo gestito è nello stato specificato dal documento di configurazione.</span><span class="sxs-lookup"><span data-stu-id="175e1-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="175e1-109">*ResourcesInDesiredState* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_ResourceInDesiredState** che specifica le risorse che si trovano nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="175e1-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="175e1-110">*ResourcesNotInDesiredState* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_ResourceNotInDesiredState** che specifica le risorse che non si trovano nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="175e1-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="175e1-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="175e1-111">Return value</span></span>

<span data-ttu-id="175e1-112">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="175e1-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="175e1-113">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="175e1-113">Remarks</span></span>

<span data-ttu-id="175e1-114">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="175e1-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="175e1-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="175e1-115">Requirements</span></span>

<span data-ttu-id="175e1-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="175e1-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="175e1-117">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="175e1-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="175e1-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="175e1-118">See also</span></span>

[<span data-ttu-id="175e1-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="175e1-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
