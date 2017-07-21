---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5d313-103">Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5d313-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5d313-104">Consente di ottenere le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5d313-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="5d313-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5d313-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="5d313-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="5d313-106">Parameters</span></span>
----------

<span data-ttu-id="5d313-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5d313-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="5d313-108">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCMetaConfiguration** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="5d313-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d313-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5d313-109">Return value</span></span>
------------

<span data-ttu-id="5d313-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="5d313-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d313-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="5d313-111">Remarks</span></span>

<span data-ttu-id="5d313-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="5d313-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d313-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5d313-113">Requirements</span></span>
------------
><span data-ttu-id="5d313-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d313-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5d313-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d313-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5d313-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5d313-116">See also</span></span>


[<span data-ttu-id="5d313-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d313-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



