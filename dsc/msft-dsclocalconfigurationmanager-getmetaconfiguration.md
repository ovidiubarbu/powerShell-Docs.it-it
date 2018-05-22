---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="baaa4-103">Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="baaa4-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="baaa4-104">Consente di ottenere le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="baaa4-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="baaa4-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="baaa4-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="baaa4-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="baaa4-106">Parameters</span></span>
----------

<span data-ttu-id="baaa4-107">*MetaConfiguration* \[out\] Al termine dell'esecuzione contiene un'istanza incorporata della classe **MSFT_DSCMetaConfiguration** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="baaa4-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="baaa4-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="baaa4-108">Return value</span></span>
------------

<span data-ttu-id="baaa4-109">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="baaa4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="baaa4-110">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="baaa4-110">Remarks</span></span>

<span data-ttu-id="baaa4-111">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="baaa4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="baaa4-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="baaa4-112">Requirements</span></span>
------------
><span data-ttu-id="baaa4-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="baaa4-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="baaa4-114">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="baaa4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="baaa4-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="baaa4-115">See also</span></span>


[<span data-ttu-id="baaa4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="baaa4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)