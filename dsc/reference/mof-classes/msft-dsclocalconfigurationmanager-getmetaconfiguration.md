---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680962"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="aa12a-103">Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="aa12a-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="aa12a-104">Consente di ottenere le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="aa12a-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa12a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aa12a-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="aa12a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="aa12a-106">Parameters</span></span>

<span data-ttu-id="aa12a-107">*MetaConfiguration* \[out\] Al termine dell'esecuzione contiene un'istanza incorporata della classe **MSFT_DSCMetaConfiguration** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="aa12a-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa12a-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="aa12a-108">Return value</span></span>

<span data-ttu-id="aa12a-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="aa12a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa12a-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="aa12a-110">Remarks</span></span>

<span data-ttu-id="aa12a-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="aa12a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa12a-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aa12a-112">Requirements</span></span>

<span data-ttu-id="aa12a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="aa12a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="aa12a-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="aa12a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="aa12a-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aa12a-115">See also</span></span>

[<span data-ttu-id="aa12a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="aa12a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)