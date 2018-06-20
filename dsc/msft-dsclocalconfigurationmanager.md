---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 615f2998b11a0a927d3868d852e0d408f500c86d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188836"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5a141-103">Classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5a141-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5a141-104">Gestione configurazione locale (LCM) che controlla lo stato dei file di configurazione e usa l'agente di configurazione per applicare le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="5a141-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="5a141-105">La sintassi seguente è semplificata dal codice MOF (Managed Object Format) e include tutte le proprietà ereditate.</span><span class="sxs-lookup"><span data-stu-id="5a141-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a141-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5a141-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="5a141-107">Members</span><span class="sxs-lookup"><span data-stu-id="5a141-107">Members</span></span>
-------

<span data-ttu-id="5a141-108">La classe **MSFT_DSCLocalConfigurationManager** ha i membri seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a141-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="5a141-109">[Metodo][]</span><span class="sxs-lookup"><span data-stu-id="5a141-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="5a141-110">Metodi</span><span class="sxs-lookup"><span data-stu-id="5a141-110">Methods</span></span>

<span data-ttu-id="5a141-111">La classe **MSFT_DSCLocalConfigurationManager** dispone di questi metodi.</span><span class="sxs-lookup"><span data-stu-id="5a141-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="5a141-112">Metodo</span><span class="sxs-lookup"><span data-stu-id="5a141-112">Method</span></span> |<span data-ttu-id="5a141-113">Description</span><span class="sxs-lookup"><span data-stu-id="5a141-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="5a141-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="5a141-115">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5a141-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="5a141-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="5a141-117">Disabilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="5a141-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="5a141-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="5a141-119">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="5a141-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="5a141-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="5a141-121">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="5a141-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="5a141-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="5a141-123">Ottiene l'output dell'agente di configurazione relativo a un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="5a141-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="5a141-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5a141-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="5a141-125">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="5a141-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="5a141-127">Ottiene le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="5a141-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="5a141-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="5a141-129">Avvia una verifica di coerenza.</span><span class="sxs-lookup"><span data-stu-id="5a141-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="5a141-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="5a141-131">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="5a141-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="5a141-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="5a141-133">Chiama direttamente il metodo di **Get** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="5a141-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="5a141-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="5a141-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="5a141-135">Chiama direttamente il metodo di **Set** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="5a141-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="5a141-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="5a141-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="5a141-137">Chiama direttamente il metodo di **Test** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="5a141-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="5a141-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="5a141-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="5a141-139">Esegue il rollback di una configurazione precedente.</span><span class="sxs-lookup"><span data-stu-id="5a141-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="5a141-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="5a141-141">Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5a141-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="5a141-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="5a141-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="5a141-143">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="5a141-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="5a141-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="5a141-145">Inviare il documento di configurazione per il nodo gestito e iniziare a usare l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="5a141-146">Usare GetConfigurationResultOutput per recuperare l'output dei risultati.</span><span class="sxs-lookup"><span data-stu-id="5a141-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="5a141-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="5a141-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="5a141-148">Configura le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5a141-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="5a141-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="5a141-150">Arresta la configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="5a141-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="5a141-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="5a141-152">Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.</span><span class="sxs-lookup"><span data-stu-id="5a141-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|





## <a name="requirements"></a><span data-ttu-id="5a141-153">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5a141-153">Requirements</span></span>
------------
><span data-ttu-id="5a141-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5a141-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5a141-155">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a141-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>