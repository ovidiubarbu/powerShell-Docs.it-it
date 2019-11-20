---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetMetaConfiguration
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953408"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="d5f02-103">Metodo GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="d5f02-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="d5f02-104">Consente di ottenere le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="d5f02-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5f02-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d5f02-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="d5f02-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="d5f02-106">Parameters</span></span>

<span data-ttu-id="d5f02-107">*MetaConfiguration* \[out\] Al termine dell'esecuzione contiene un'istanza incorporata della classe **MSFT_DSCMetaConfiguration** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="d5f02-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d5f02-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d5f02-108">Return value</span></span>

<span data-ttu-id="d5f02-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="d5f02-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5f02-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="d5f02-110">Remarks</span></span>

<span data-ttu-id="d5f02-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="d5f02-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5f02-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d5f02-112">Requirements</span></span>

<span data-ttu-id="d5f02-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d5f02-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d5f02-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d5f02-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d5f02-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5f02-115">See also</span></span>

[<span data-ttu-id="d5f02-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d5f02-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)