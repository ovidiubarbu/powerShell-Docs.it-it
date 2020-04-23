---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953268"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a><span data-ttu-id="709c5-103">Classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="709c5-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="709c5-104">Gestione configurazione locale (LCM) che controlla lo stato dei file di configurazione e usa l'agente di configurazione per applicare le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="709c5-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="709c5-105">La sintassi seguente è semplificata dal codice MOF (Managed Object Format) e include tutte le proprietà ereditate.</span><span class="sxs-lookup"><span data-stu-id="709c5-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="709c5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="709c5-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="709c5-107">Members</span><span class="sxs-lookup"><span data-stu-id="709c5-107">Members</span></span>

<span data-ttu-id="709c5-108">La classe **MSFT_DSCLocalConfigurationManager** ha i membri seguenti:</span><span class="sxs-lookup"><span data-stu-id="709c5-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="709c5-109">[Metodo][]</span><span class="sxs-lookup"><span data-stu-id="709c5-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="709c5-110">Metodi</span><span class="sxs-lookup"><span data-stu-id="709c5-110">Methods</span></span>

<span data-ttu-id="709c5-111">La classe **MSFT_DSCLocalConfigurationManager** dispone di questi metodi.</span><span class="sxs-lookup"><span data-stu-id="709c5-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="709c5-112">Metodo</span><span class="sxs-lookup"><span data-stu-id="709c5-112">Method</span></span> |<span data-ttu-id="709c5-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="709c5-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="709c5-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="709c5-115">Usa l'agente di configurazione per applicare la configurazione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="709c5-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="709c5-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="709c5-117">Disabilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="709c5-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="709c5-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="709c5-119">Abilita il debug delle risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="709c5-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="709c5-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="709c5-121">Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="709c5-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="709c5-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="709c5-123">Ottiene l'output dell'agente di configurazione relativo a un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="709c5-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="709c5-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="709c5-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="709c5-125">Ottenere la cronologia dello stato della configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="709c5-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="709c5-127">Ottiene le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="709c5-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="709c5-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="709c5-129">Avvia una verifica di coerenza.</span><span class="sxs-lookup"><span data-stu-id="709c5-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="709c5-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="709c5-131">Rimuove i file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="709c5-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="709c5-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="709c5-133">Chiama direttamente il metodo di **Get** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="709c5-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="709c5-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="709c5-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="709c5-135">Chiama direttamente il metodo di **Set** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="709c5-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="709c5-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="709c5-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="709c5-137">Chiama direttamente il metodo di **Test** di una risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="709c5-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="709c5-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="709c5-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="709c5-139">Esegue il rollback di una configurazione precedente.</span><span class="sxs-lookup"><span data-stu-id="709c5-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="709c5-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="709c5-141">Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.</span><span class="sxs-lookup"><span data-stu-id="709c5-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="709c5-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="709c5-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="709c5-143">Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="709c5-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="709c5-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="709c5-145">Inviare il documento di configurazione per il nodo gestito e iniziare a usare l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="709c5-146">Usare GetConfigurationResultOutput per recuperare l'output dei risultati.</span><span class="sxs-lookup"><span data-stu-id="709c5-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="709c5-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="709c5-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="709c5-148">Configura le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.</span><span class="sxs-lookup"><span data-stu-id="709c5-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="709c5-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="709c5-150">Arresta la configurazione in corso.</span><span class="sxs-lookup"><span data-stu-id="709c5-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="709c5-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="709c5-152">Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.</span><span class="sxs-lookup"><span data-stu-id="709c5-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="709c5-153">Requisiti</span><span class="sxs-lookup"><span data-stu-id="709c5-153">Requirements</span></span>

<span data-ttu-id="709c5-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="709c5-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="709c5-155">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="709c5-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
