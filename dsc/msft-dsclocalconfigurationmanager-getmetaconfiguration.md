---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9db93-103">Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9db93-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9db93-104">Consente di ottenere le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9db93-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="9db93-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9db93-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="9db93-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9db93-106">Parameters</span></span>
----------

<span data-ttu-id="9db93-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9db93-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="9db93-108">In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCMetaConfiguration** che definisce le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="9db93-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9db93-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="9db93-109">Return value</span></span>
------------

<span data-ttu-id="9db93-110">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="9db93-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9db93-111">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="9db93-111">Remarks</span></span>

<span data-ttu-id="9db93-112">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="9db93-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9db93-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9db93-113">Requirements</span></span>
------------
><span data-ttu-id="9db93-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9db93-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9db93-115">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9db93-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9db93-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9db93-116">See also</span></span>


[<span data-ttu-id="9db93-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9db93-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



