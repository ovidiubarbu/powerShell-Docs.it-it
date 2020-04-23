---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Procedure consigliate per i server di pull
ms.openlocfilehash: b2469984086a827b6b2a0fe84d1f326fc214ec28
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500690"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="53f26-103">Procedure consigliate per i server di pull</span><span class="sxs-lookup"><span data-stu-id="53f26-103">Pull server best practices</span></span>

<span data-ttu-id="53f26-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="53f26-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53f26-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="53f26-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="53f26-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="53f26-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="53f26-107">Riepilogo: questo documento illustra processi ed estendibilità per supportare i tecnici che preparano la soluzione.</span><span class="sxs-lookup"><span data-stu-id="53f26-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="53f26-108">I dettagli inclusi offrono procedure consigliate identificate dai clienti e validate dal team del prodotto per garantire che le indicazioni siano stabili e valide per il futuro.</span><span class="sxs-lookup"><span data-stu-id="53f26-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

|           |                      <span data-ttu-id="53f26-109">Informazioni sul documento</span><span class="sxs-lookup"><span data-stu-id="53f26-109">Doc Info</span></span>                      |
| :-------- | :------------------------------------------------- |
| <span data-ttu-id="53f26-110">Autore</span><span class="sxs-lookup"><span data-stu-id="53f26-110">Author</span></span>    | <span data-ttu-id="53f26-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="53f26-111">Michael Greene</span></span>                                     |
| <span data-ttu-id="53f26-112">Revisori</span><span class="sxs-lookup"><span data-stu-id="53f26-112">Reviewers</span></span> | <span data-ttu-id="53f26-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="53f26-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span> |
| <span data-ttu-id="53f26-114">Pubblicato</span><span class="sxs-lookup"><span data-stu-id="53f26-114">Published</span></span> | <span data-ttu-id="53f26-115">Aprile 2015</span><span class="sxs-lookup"><span data-stu-id="53f26-115">April, 2015</span></span>                                        |

## <a name="abstract"></a><span data-ttu-id="53f26-116">Contenuto</span><span class="sxs-lookup"><span data-stu-id="53f26-116">Abstract</span></span>

<span data-ttu-id="53f26-117">Questo documento è designato a offrire procedure ufficiali a coloro che pianificano di implementare un server di pull per la configurazione dello stato desiderato tramite Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53f26-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="53f26-118">Un server di pull è un servizio semplice, la cui distribuzione dovrebbe impiegare solo alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="53f26-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="53f26-119">Sebbene questo documento includa procedure tecniche che possono essere usate in una distribuzione, il suo scopo è di essere un riferimento per procedure consigliate e per gli elementi da considerare prima di eseguire una distribuzione.</span><span class="sxs-lookup"><span data-stu-id="53f26-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span> <span data-ttu-id="53f26-120">I lettori devono avere una conoscenza di base di DSC e dei termini usati per descrivere i componenti inclusi in una distribuzione DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="53f26-121">Per altre informazioni, vedere l'argomento [Panoramica di Windows PowerShell DSC (Desired State Configuration)](/powershell/scripting/dsc/overview/overview).</span><span class="sxs-lookup"><span data-stu-id="53f26-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) topic.</span></span> <span data-ttu-id="53f26-122">Poiché si presuppone che DSC evolverà presto verso una cadenza cloud, la tecnologia che sta alla base, inclusi i server di pull, evolverà e presenterà nuove funzionalità.</span><span class="sxs-lookup"><span data-stu-id="53f26-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="53f26-123">Questo documento include nell'appendice una tabella delle versioni, che offre riferimenti a versioni precedenti e a soluzioni future per incoraggiare la creazione di strutture che guardano al futuro.</span><span class="sxs-lookup"><span data-stu-id="53f26-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="53f26-124">Le due sezioni principali di questo documento sono:</span><span class="sxs-lookup"><span data-stu-id="53f26-124">The two major sections of this document:</span></span>

- <span data-ttu-id="53f26-125">Pianificazione della configurazione</span><span class="sxs-lookup"><span data-stu-id="53f26-125">Configuration Planning</span></span>
- <span data-ttu-id="53f26-126">Guida all'installazione</span><span class="sxs-lookup"><span data-stu-id="53f26-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="53f26-127">Versioni di Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="53f26-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="53f26-128">Le informazioni contenute in questo documento sono applicabili a Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="53f26-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="53f26-129">Anche se WMF 5.0 non è necessario per la distribuzione e l'operatività di un server di pull, in questo documento si fa riferimento alla versione 5.0.</span><span class="sxs-lookup"><span data-stu-id="53f26-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="53f26-130">Configurazione dello stato desiderato tramite Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="53f26-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="53f26-131">La configurazione dello stato desiderato (DSC) è una piattaforma di gestione che consente la distribuzione e la gestione dei dati di configurazione usando una sintassi standard, denominata Managed Object Format (MOF) per descrivere Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="53f26-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="53f26-132">Un progetto open source, Open Management Infrastructure (OMI), è disponibile per altri sviluppi di tali standard tra piattaforme, ad esempio Linux e sistemi operativi per hardware di rete.</span><span class="sxs-lookup"><span data-stu-id="53f26-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="53f26-133">Per altre informazioni, vedere la [pagina DMTF con il collegamento alle specifiche MOF](https://www.dmtf.org/standards/cim) e la pagina che elenca i [documenti e le origine OMI](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="53f26-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="53f26-134">Windows PowerShell offre un set di estensioni del linguaggio per la configurazione dello stato desiderato che è possibile usare per creare e gestire configurazioni dichiarative.</span><span class="sxs-lookup"><span data-stu-id="53f26-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="53f26-135">Ruolo del server di pull</span><span class="sxs-lookup"><span data-stu-id="53f26-135">Pull server role</span></span>

<span data-ttu-id="53f26-136">Un server di pull offre un servizio centralizzato per archiviare le configurazioni che saranno accessibili per i nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="53f26-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="53f26-137">Il ruolo del server di pull può essere distribuito come istanza del server Web o come condivisione di file SMB.</span><span class="sxs-lookup"><span data-stu-id="53f26-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="53f26-138">La funzionalità del server Web include un'interfaccia OData e può facoltativamente includere funzionalità per i nodi di destinazione per restituire la conferma di un esito positivo o negativo quando vengono applicate le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="53f26-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="53f26-139">Questa funzionalità è utile in ambienti in cui è presente un numero elevato di nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="53f26-139">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="53f26-140">Dopo la configurazione di un nodo di destinazione (noto anche come client) verso il server di pull, vengono scaricati e applicati i dati della configurazione più recente e gli script necessari.</span><span class="sxs-lookup"><span data-stu-id="53f26-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="53f26-141">Questa operazione può essere eseguita come distribuzione singola o come processo ripetuto. Ciò rende il server di pull un'importante risorsa per la gestione di modifiche su larga scala.</span><span class="sxs-lookup"><span data-stu-id="53f26-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="53f26-142">Per altre informazioni, vedere [Windows PowerShell Desired State Configuration Pull Servers](pullserver.md) (Server di pull per la configurazione dello stato desiderato tramite Windows PowerShell) e [Push and Pull Configuration Modes](pullserver.md) (Modalità di configurazione push e pull).</span><span class="sxs-lookup"><span data-stu-id="53f26-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](pullserver.md) and [Push and Pull Configuration Modes](pullserver.md).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="53f26-143">Pianificazione della configurazione</span><span class="sxs-lookup"><span data-stu-id="53f26-143">Configuration planning</span></span>

<span data-ttu-id="53f26-144">Per la distribuzione di software aziendale, alcune informazioni possono essere raccolte in anticipo per supportare la pianificazione dell'architettura appropriata e per essere pronti ai passaggi necessari per completare la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="53f26-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="53f26-145">Le sezioni seguenti includono informazioni su come preparare la distribuzione e le connessioni organizzative che dovranno probabilmente essere eseguite in anticipo.</span><span class="sxs-lookup"><span data-stu-id="53f26-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="53f26-146">Requisiti software</span><span class="sxs-lookup"><span data-stu-id="53f26-146">Software requirements</span></span>

<span data-ttu-id="53f26-147">La distribuzione di un server di pull richiede la funzionalità del servizio DSC di Windows Server.</span><span class="sxs-lookup"><span data-stu-id="53f26-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="53f26-148">Questa funzionalità è stata introdotta in Windows Server 2012 ed è stata aggiornata tramite le versioni in corso di Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="53f26-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="53f26-149">Download del software</span><span class="sxs-lookup"><span data-stu-id="53f26-149">Software downloads</span></span>

<span data-ttu-id="53f26-150">Oltre a installare i contenuti più recenti da Windows Update, per distribuire un server di pull DSC è consigliabile scaricare la versione più recente di Windows Management Framework e un modulo DSC per automatizzare il provisioning del server di pull.</span><span class="sxs-lookup"><span data-stu-id="53f26-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="53f26-151">WMF</span><span class="sxs-lookup"><span data-stu-id="53f26-151">WMF</span></span>

<span data-ttu-id="53f26-152">Windows Server 2012 R2 include una funzionalità denominata servizio DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="53f26-153">La caratteristica servizio DSC offre la funzionalità del server di pull, inclusi i file binari che supportano l'endpoint OData.</span><span class="sxs-lookup"><span data-stu-id="53f26-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="53f26-154">WMF è incluso in Windows Server e viene aggiornato regolarmente tra le versioni di Windows Server.</span><span class="sxs-lookup"><span data-stu-id="53f26-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span>
<span data-ttu-id="53f26-155">Le [nuove versioni di WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) possono includere aggiornamenti per la funzionalità del servizio DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-155">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) can include updates to the DSC Service feature.</span></span> <span data-ttu-id="53f26-156">Per questo motivo, è consigliabile scaricare la versione più recente di WMF ed esaminare le note sulla versione per determinare se la versione include un aggiornamento per la funzionalità servizio DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="53f26-157">È anche necessario esaminare la sezione delle note sulla versione che indica se lo stato di progettazione per uno scenario o per un aggiornamento è elencato come stabile o sperimentale.</span><span class="sxs-lookup"><span data-stu-id="53f26-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="53f26-158">Per consentire un ciclo di versioni agile, le singole funzionalità possono essere dichiarate stabili, ovvero sono pronte per essere usate in un ambiente di produzione, anche se WMF viene rilasciato in anteprima.</span><span class="sxs-lookup"><span data-stu-id="53f26-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span> <span data-ttu-id="53f26-159">Altre funzionalità che storicamente sono state aggiornate dalle versioni di WMF (per altre informazioni, vedere le note sulla versione WMF):</span><span class="sxs-lookup"><span data-stu-id="53f26-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="53f26-160">Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="53f26-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="53f26-161">Servizi Web di Windows PowerShell (Estensione IIS OData gestione)</span><span class="sxs-lookup"><span data-stu-id="53f26-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="53f26-162">Configurazione dello stato desiderato tramite Windows PowerShell (DSC)</span><span class="sxs-lookup"><span data-stu-id="53f26-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="53f26-163">Gestione remota Windows (WinRM) Strumentazione gestione Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="53f26-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="53f26-164">Risorsa DSC</span><span class="sxs-lookup"><span data-stu-id="53f26-164">DSC resource</span></span>

<span data-ttu-id="53f26-165">Una distribuzione del server di pull può essere semplificata dal provisioning del servizio tramite uno script di configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="53f26-166">Questo documento include gli script di configurazione che possono essere usati per distribuire un nodo server pronto per la produzione.</span><span class="sxs-lookup"><span data-stu-id="53f26-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="53f26-167">Per usare gli script di configurazione, è necessario un modulo DSC non incluso in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="53f26-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="53f26-168">Il nome del modulo necessario è **xPSDesiredStateConfiguration**, il quale include la risorsa DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="53f26-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="53f26-169">È possibile scaricare il modulo xPSDesiredStateConfiguration [qui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="53f26-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="53f26-170">Usare il cmdlet `Install-Module` dal modulo **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="53f26-170">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="53f26-171">Il modulo **PowerShellGet** scaricherà il modulo in:</span><span class="sxs-lookup"><span data-stu-id="53f26-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="53f26-172">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-172">Planning task</span></span>
- <span data-ttu-id="53f26-173">Si ha accesso ai file di installazione di Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="53f26-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>
- <span data-ttu-id="53f26-174">L'ambiente di distribuzione ha accesso a Internet per scaricare WMF e il modulo dalla raccolta online?</span><span class="sxs-lookup"><span data-stu-id="53f26-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>
- <span data-ttu-id="53f26-175">Come si installeranno gli aggiornamenti più recenti dopo l'installazione del sistema operativo?</span><span class="sxs-lookup"><span data-stu-id="53f26-175">How will you install the latest security updates after installing the operating system?</span></span>
- <span data-ttu-id="53f26-176">L'ambiente avrà accesso a Internet per ottenere gli aggiornamenti oppure avrà un server locale Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="53f26-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>
- <span data-ttu-id="53f26-177">Si ha accesso ai file di installazione di Windows Server che includono già gli aggiornamenti tramite un'aggiunta offline?</span><span class="sxs-lookup"><span data-stu-id="53f26-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>

### <a name="hardware-requirements"></a><span data-ttu-id="53f26-178">Requisiti hardware</span><span class="sxs-lookup"><span data-stu-id="53f26-178">Hardware requirements</span></span>

<span data-ttu-id="53f26-179">Le distribuzioni di server di pull sono supportate nei server fisici e virtuali.</span><span class="sxs-lookup"><span data-stu-id="53f26-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="53f26-180">I requisiti di dimensioni per il server di pull si allineano con i requisiti per Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="53f26-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

- <span data-ttu-id="53f26-181">CPU: processore da 1,4 GHz a 64 bit</span><span class="sxs-lookup"><span data-stu-id="53f26-181">CPU: 1.4 GHz 64-bit processor</span></span>
- <span data-ttu-id="53f26-182">Memoria: 512 MB</span><span class="sxs-lookup"><span data-stu-id="53f26-182">Memory: 512 MB</span></span>
- <span data-ttu-id="53f26-183">Spazio su disco: 32 GB</span><span class="sxs-lookup"><span data-stu-id="53f26-183">Disk Space: 32 GB</span></span>
- <span data-ttu-id="53f26-184">Rete: scheda Gigabit Ethernet</span><span class="sxs-lookup"><span data-stu-id="53f26-184">Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="53f26-185">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-185">Planning task</span></span>
- <span data-ttu-id="53f26-186">La distribuzione verrà eseguita in hardware fisico o su una piattaforma di virtualizzazione?</span><span class="sxs-lookup"><span data-stu-id="53f26-186">Will you deploy on physical hardware or on a virtualization platform?</span></span>
- <span data-ttu-id="53f26-187">Qual è il processo per richiedere un nuovo server per l'ambiente di destinazione?</span><span class="sxs-lookup"><span data-stu-id="53f26-187">What is the process to request a new server for your target environment?</span></span>
- <span data-ttu-id="53f26-188">Qual è il tempo medio necessario a un server per essere disponibile?</span><span class="sxs-lookup"><span data-stu-id="53f26-188">What is the average turnaround time for a server to become available?</span></span>
- <span data-ttu-id="53f26-189">Quali dimensioni del server saranno richieste?</span><span class="sxs-lookup"><span data-stu-id="53f26-189">What size server will you request?</span></span>

### <a name="accounts"></a><span data-ttu-id="53f26-190">Account</span><span class="sxs-lookup"><span data-stu-id="53f26-190">Accounts</span></span>

<span data-ttu-id="53f26-191">Non sono previsti requisiti di account di servizio per distribuire un'istanza del server di pull.</span><span class="sxs-lookup"><span data-stu-id="53f26-191">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="53f26-192">Ci sono tuttavia scenari in cui il sito Web può essere eseguito nel contesto di un account utente locale.</span><span class="sxs-lookup"><span data-stu-id="53f26-192">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="53f26-193">Ad esempio, se è necessario accedere a una condivisione di archiviazione per il contenuto del sito Web e Windows Server o il dispositivo che ospita la condivisione di archiviazione non sono aggiunti a un dominio.</span><span class="sxs-lookup"><span data-stu-id="53f26-193">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="53f26-194">Record DNS</span><span class="sxs-lookup"><span data-stu-id="53f26-194">DNS records</span></span>

<span data-ttu-id="53f26-195">È necessario avere un nome di server quando si configurano i client che usano un ambiente server di pull.</span><span class="sxs-lookup"><span data-stu-id="53f26-195">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="53f26-196">In ambienti di test, viene in genere usato il nome host del server oppure può essere usato l'indirizzo IP per il server se la risoluzione dei nomi DNS non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="53f26-196">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="53f26-197">Negli ambienti di produzione o in un ambiente lab che ha lo scopo di rappresentare una distribuzione di produzione, la procedura consigliata consiste nel creare un record CNAME DNS.</span><span class="sxs-lookup"><span data-stu-id="53f26-197">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="53f26-198">Un CNAME DNS consente di creare un alias come riferimento al record dell'host (A).</span><span class="sxs-lookup"><span data-stu-id="53f26-198">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="53f26-199">Lo scopo del record del nome aggiuntivo è incrementare la flessibilità, se dovesse essere necessaria una modifica in futuro.</span><span class="sxs-lookup"><span data-stu-id="53f26-199">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="53f26-200">Un CNAME consente di isolare la configurazione del client in modo che le modifiche all'ambiente di server, ad esempio la sostituzione di un server di pull o l'aggiunta di altri server di pull, non richiedano una modifica corrispondente alla configurazione del client.</span><span class="sxs-lookup"><span data-stu-id="53f26-200">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="53f26-201">Quando si sceglie un nome per il record DNS, tenere presente l'architettura della soluzione.</span><span class="sxs-lookup"><span data-stu-id="53f26-201">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="53f26-202">Se si usa il bilanciamento del carico, il certificato usato per proteggere il traffico su HTTPS deve condividere lo stesso nome del record DNS.</span><span class="sxs-lookup"><span data-stu-id="53f26-202">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

       <span data-ttu-id="53f26-203">Scenario</span><span class="sxs-lookup"><span data-stu-id="53f26-203">Scenario</span></span>        |                                                                                         <span data-ttu-id="53f26-204">Procedura consigliata</span><span class="sxs-lookup"><span data-stu-id="53f26-204">Best Practice</span></span>
:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="53f26-205">Ambiente di test</span><span class="sxs-lookup"><span data-stu-id="53f26-205">Test Environment</span></span>       | <span data-ttu-id="53f26-206">Riprodurre l'ambiente di produzione pianificato, se possibile.</span><span class="sxs-lookup"><span data-stu-id="53f26-206">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="53f26-207">Un nome host del server è adatto per configurazioni semplici.</span><span class="sxs-lookup"><span data-stu-id="53f26-207">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="53f26-208">Se DNS non è disponibile, può essere usato un indirizzo IP anziché un nome host.</span><span class="sxs-lookup"><span data-stu-id="53f26-208">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>
<span data-ttu-id="53f26-209">Distribuzione di un nodo singolo</span><span class="sxs-lookup"><span data-stu-id="53f26-209">Single Node Deployment</span></span> | <span data-ttu-id="53f26-210">Creare un record CNAME DNS che punta al nome host del server.</span><span class="sxs-lookup"><span data-stu-id="53f26-210">Create a DNS CNAME record that points to the server hostname.</span></span>

<span data-ttu-id="53f26-211">Per altre informazioni, vedere [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)) (Configurazione del round robin DNS in Windows Server).</span><span class="sxs-lookup"><span data-stu-id="53f26-211">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="53f26-212">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-212">Planning task</span></span>
- <span data-ttu-id="53f26-213">Si sa a chi rivolgersi per avere i record DNS creati e modificati?</span><span class="sxs-lookup"><span data-stu-id="53f26-213">Do you know who to contact to have DNS records created and changed?</span></span>
- <span data-ttu-id="53f26-214">Qual è il tempo medio per una richiesta di un record DNS?</span><span class="sxs-lookup"><span data-stu-id="53f26-214">What is the average turnaround for a request for a DNS record?</span></span>
- <span data-ttu-id="53f26-215">È necessario richiedere record di nome host (A) statici per i server?</span><span class="sxs-lookup"><span data-stu-id="53f26-215">Do you need to request static Hostname (A) records for servers?</span></span>
- <span data-ttu-id="53f26-216">Cosa verrà richiesto come CNAME?</span><span class="sxs-lookup"><span data-stu-id="53f26-216">What will you request as a CNAME?</span></span>
- <span data-ttu-id="53f26-217">Se necessario, quale tipo di soluzione di bilanciamento del carico verrà usato?</span><span class="sxs-lookup"><span data-stu-id="53f26-217">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="53f26-218">(vedere la sezione Bilanciamento del carico per informazioni dettagliate)</span><span class="sxs-lookup"><span data-stu-id="53f26-218">(see section titled Load Balancing for details)</span></span>

### <a name="public-key-infrastructure"></a><span data-ttu-id="53f26-219">Infrastruttura a chiave pubblica (PKI)</span><span class="sxs-lookup"><span data-stu-id="53f26-219">Public Key Infrastructure</span></span>

<span data-ttu-id="53f26-220">La maggior parte delle organizzazioni richiedono oggi che il traffico di rete, in particolare il traffico che include dati sensibili, ad esempio la configurazione dei server, debba essere validato e/o crittografato durante il trasferimento.</span><span class="sxs-lookup"><span data-stu-id="53f26-220">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="53f26-221">Sebbene sia possibile distribuire un server di pull tramite HTTP che facilita le richieste client in testo non crittografato, è consigliabile proteggere il traffico tramite HTTPS.</span><span class="sxs-lookup"><span data-stu-id="53f26-221">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="53f26-222">Il servizio può essere configurato per l'uso di HTTPS tramite un set di parametri nella risorsa DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="53f26-222">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="53f26-223">I requisiti del certificato per proteggere il traffico HTTPS per il server di pull non sono diversi da quelli per la protezione di qualsiasi altro sito Web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="53f26-223">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="53f26-224">Il modello **Web Server** in Servizi certificati di Windows Server soddisfa le funzionalità necessarie.</span><span class="sxs-lookup"><span data-stu-id="53f26-224">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="53f26-225">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-225">Planning task</span></span>
- <span data-ttu-id="53f26-226">Se le richieste di certificati non sono automatiche, a chi è necessario rivolgersi per richiedere un certificato?</span><span class="sxs-lookup"><span data-stu-id="53f26-226">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>
- <span data-ttu-id="53f26-227">Qual è il tempo medio di elaborazione della richiesta?</span><span class="sxs-lookup"><span data-stu-id="53f26-227">What is the average turnaround for the request?</span></span>
- <span data-ttu-id="53f26-228">Come verrà trasferito il file del certificato all'utente?</span><span class="sxs-lookup"><span data-stu-id="53f26-228">How will the certificate file be transferred to you?</span></span>
- <span data-ttu-id="53f26-229">Come verrà trasferita la chiave privata del certificato all'utente?</span><span class="sxs-lookup"><span data-stu-id="53f26-229">How will the certificate private key be transferred to you?</span></span>
- <span data-ttu-id="53f26-230">Qual è il periodo di tempo predefinito prima della scadenza?</span><span class="sxs-lookup"><span data-stu-id="53f26-230">How long is the default expiration time?</span></span>
- <span data-ttu-id="53f26-231">È stato definito un nome DNS per l'ambiente del server del pull, che è possibile usare per il nome certificato?</span><span class="sxs-lookup"><span data-stu-id="53f26-231">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>

### <a name="choosing-an-architecture"></a><span data-ttu-id="53f26-232">Scelta di un'architettura</span><span class="sxs-lookup"><span data-stu-id="53f26-232">Choosing an architecture</span></span>

<span data-ttu-id="53f26-233">Un server di pull può essere distribuito tramite un servizio Web ospitato in IIS o tramite una condivisione file SMB.</span><span class="sxs-lookup"><span data-stu-id="53f26-233">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="53f26-234">Nella maggior parte dei casi, l'uso del servizio Web offre maggiore flessibilità.</span><span class="sxs-lookup"><span data-stu-id="53f26-234">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="53f26-235">Non è insolito che il traffico HTTPS oltrepassi i limiti di rete, mentre il traffico SMB è spesso filtrato o bloccato tra le reti.</span><span class="sxs-lookup"><span data-stu-id="53f26-235">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="53f26-236">Il servizio Web offre anche l'opzione di includere un server di conformità o Gestione rapporti Web (entrambi gli argomenti verranno trattati in una versione futura di questo documento) che offrono ai client un meccanismo di restituire lo stato a un server per una visibilità centralizzata.</span><span class="sxs-lookup"><span data-stu-id="53f26-236">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="53f26-237">SMB offre un'opzione per alcuni ambienti in cui i criteri indicano che un server Web non debba essere usato e per altri ambienti che rendono il ruolo del server Web indesiderato.</span><span class="sxs-lookup"><span data-stu-id="53f26-237">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="53f26-238">In entrambi i casi, è necessario valutare i requisiti per la firma e la crittografia del traffico.</span><span class="sxs-lookup"><span data-stu-id="53f26-238">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="53f26-239">HTTPS, firma SMB e criteri IPSEC sono tutte opzioni da considerare.</span><span class="sxs-lookup"><span data-stu-id="53f26-239">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="53f26-240">Bilanciamento del carico</span><span class="sxs-lookup"><span data-stu-id="53f26-240">Load balancing</span></span>

<span data-ttu-id="53f26-241">I client che interagiscono con il servizio Web eseguono una richiesta di informazioni restituita in una risposta singola.</span><span class="sxs-lookup"><span data-stu-id="53f26-241">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="53f26-242">Nessuna richiesta sequenziale è obbligatoria, pertanto non è necessario assicurarsi che per la piattaforma del bilanciamento del carico siano sempre mantenute le sessioni in un server singolo.</span><span class="sxs-lookup"><span data-stu-id="53f26-242">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="53f26-243">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-243">Planning task</span></span>
- <span data-ttu-id="53f26-244">Quale soluzione verrà usata per il traffico del bilanciamento del carico tra server?</span><span class="sxs-lookup"><span data-stu-id="53f26-244">What solution will be used for load balancing traffic across servers?</span></span>
- <span data-ttu-id="53f26-245">Se si usa un bilanciamento del carico hardware, chi prenderà la richiesta per aggiungere una nuova configurazione al dispositivo?</span><span class="sxs-lookup"><span data-stu-id="53f26-245">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>
- <span data-ttu-id="53f26-246">Qual è il tempo medio di elaborazione di una richiesta per configurare un nuovo servizio Web con carico bilanciato?</span><span class="sxs-lookup"><span data-stu-id="53f26-246">What is the average turnaround for a request to configure a new load balanced web service?</span></span>
- <span data-ttu-id="53f26-247">Quali informazioni sono necessarie per la richiesta?</span><span class="sxs-lookup"><span data-stu-id="53f26-247">What information will be required for the request?</span></span>
- <span data-ttu-id="53f26-248">Sarà necessario richiedere un indirizzo IP aggiuntivo o il team responsabile del bilanciamento del carico gestirà l'operazione?</span><span class="sxs-lookup"><span data-stu-id="53f26-248">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>
- <span data-ttu-id="53f26-249">Si hanno i record DNS necessari? Questa disponibilità verrà richiesta dal team responsabile della configurazione della soluzione di bilanciamento del carico?</span><span class="sxs-lookup"><span data-stu-id="53f26-249">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>
- <span data-ttu-id="53f26-250">La soluzione di bilanciamento del carico richiede che PKI sia gestito dal dispositivo o può bilanciare il carico del traffico HTTPS se non ci sono requisiti di sessione?</span><span class="sxs-lookup"><span data-stu-id="53f26-250">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="53f26-251">Gestione temporanea di configurazioni e moduli nel server di pull</span><span class="sxs-lookup"><span data-stu-id="53f26-251">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="53f26-252">Come parte della pianificazione della configurazione, è necessario determinare quali moduli e configurazioni DSC verranno ospitati dal server di pull.</span><span class="sxs-lookup"><span data-stu-id="53f26-252">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="53f26-253">Ai fini della pianificazione della configurazione è importante avere una conoscenza di base su come preparare e distribuire contenuto a un server di pull.</span><span class="sxs-lookup"><span data-stu-id="53f26-253">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="53f26-254">In futuro, questa sezione verrà estesa e inclusa in una guida operativa per il server di pull DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-254">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span> <span data-ttu-id="53f26-255">La guida illustrerà il processo quotidiano per la gestione di moduli e configurazioni nel tempo con l'automazione.</span><span class="sxs-lookup"><span data-stu-id="53f26-255">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="53f26-256">Moduli DSC</span><span class="sxs-lookup"><span data-stu-id="53f26-256">DSC modules</span></span>

<span data-ttu-id="53f26-257">I client che richiedono una configurazione avranno bisogno dei moduli DSC richiesti.</span><span class="sxs-lookup"><span data-stu-id="53f26-257">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="53f26-258">Una funzionalità del server di pull consiste nell'automatizzare la distribuzione su richiesta dei moduli DSC ai client.</span><span class="sxs-lookup"><span data-stu-id="53f26-258">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="53f26-259">Se si distribuisce un server di pull per la prima volta, ad esempio come lab o modello di verifica, probabilmente si dipenderà dai moduli DSC che sono disponibili nei repository pubblici, ad esempio la raccolta di PowerShell o i repository GitHub di PowerShell.org per i moduli DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-259">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="53f26-260">È fondamentale ricordare che anche per le origini online attendibile, ad esempio PowerShell Gallery, ogni modulo che viene scaricato da un repository pubblico deve essere esaminato da un utente con esperienza in PowerShell e conoscenza dell'ambiente in cui i moduli verranno usati prima di essere usati nell'ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="53f26-260">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="53f26-261">Durante il completamento di questa attività, è consigliabile verificare la presenza di eventuali payload aggiuntivi nel modulo che possono essere rimossi, ad esempio gli script di esempio e la documentazione.</span><span class="sxs-lookup"><span data-stu-id="53f26-261">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="53f26-262">Ciò riduce la larghezza di banda di rete per ogni client durante la prima richiesta, quando i moduli verranno scaricati nella rete dal server al client.</span><span class="sxs-lookup"><span data-stu-id="53f26-262">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="53f26-263">Ogni modulo deve essere compresso in un formato specifico, ovvero un file ZIP denominato nomemodulo_versione.zip, che contenga il payload del modulo.</span><span class="sxs-lookup"><span data-stu-id="53f26-263">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="53f26-264">Dopo che il file viene copiato nel server, è necessario creare un file di checksum.</span><span class="sxs-lookup"><span data-stu-id="53f26-264">After the file is copied to the server a checksum file must be created.</span></span>
<span data-ttu-id="53f26-265">Quando i client si connettono al server, viene usato il checksum per verificare che il contenuto del modulo DSC non è stato modificato dopo la pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="53f26-265">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="53f26-266">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-266">Planning task</span></span>
- <span data-ttu-id="53f26-267">Se si pianifica un ambiente di test o lab, quali sono gli scenari fondamentali da convalidare?</span><span class="sxs-lookup"><span data-stu-id="53f26-267">If you are planning a test or lab environment which scenarios are key to validate?</span></span>
- <span data-ttu-id="53f26-268">Sono disponibili pubblicamente i moduli che contengono le risorse necessarie per coprire tutto ciò che è necessario o si devono creare le proprie risorse?</span><span class="sxs-lookup"><span data-stu-id="53f26-268">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>
- <span data-ttu-id="53f26-269">L'ambiente avrà accesso a Internet per recuperare i moduli pubblici?</span><span class="sxs-lookup"><span data-stu-id="53f26-269">Will your environment have Internet access to retrieve public modules?</span></span>
- <span data-ttu-id="53f26-270">Chi sarà responsabile della revisione dei moduli DSC?</span><span class="sxs-lookup"><span data-stu-id="53f26-270">Who will be responsible for reviewing DSC modules?</span></span>
- <span data-ttu-id="53f26-271">Se si pianifica un ambiente di produzione, che cosa verrà usato come repository locale per l'archiviazione dei moduli DSC?</span><span class="sxs-lookup"><span data-stu-id="53f26-271">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>
- <span data-ttu-id="53f26-272">Un team centrale accetterà moduli DSC provenienti dai team dell'applicazione?</span><span class="sxs-lookup"><span data-stu-id="53f26-272">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="53f26-273">Quale sarà il processo?</span><span class="sxs-lookup"><span data-stu-id="53f26-273">What will the process be?</span></span>
- <span data-ttu-id="53f26-274">Verranno automatizzati l'assemblaggio, la copia e la creazione di un checksum per i moduli DSC pronti alla produzione dal repository di origine al server?</span><span class="sxs-lookup"><span data-stu-id="53f26-274">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>
- <span data-ttu-id="53f26-275">Il team sarà anche responsabile per la gestione della piattaforma di automazione?</span><span class="sxs-lookup"><span data-stu-id="53f26-275">Will your team be responsible for managing the automation platform as well?</span></span>

#### <a name="dsc-configurations"></a><span data-ttu-id="53f26-276">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="53f26-276">DSC configurations</span></span>

<span data-ttu-id="53f26-277">Lo scopo di un server di pull è fornire un meccanismo centralizzato per la distribuzione delle configurazioni DSC ai nodi client.</span><span class="sxs-lookup"><span data-stu-id="53f26-277">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="53f26-278">Le configurazioni sono archiviate nel server come documenti MOF.</span><span class="sxs-lookup"><span data-stu-id="53f26-278">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="53f26-279">Ogni documento verrà denominato con un identificatore univoco globale (**GUID**).</span><span class="sxs-lookup"><span data-stu-id="53f26-279">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="53f26-280">Quando i client vengono configurati per la connessione a un server di pull, viene assegnato l'identificatore **GUID** per la configurazione che i client devono richiedere.</span><span class="sxs-lookup"><span data-stu-id="53f26-280">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="53f26-281">Questo sistema di riferimento a configurazioni da identificatori **GUID** garantisce l'univocità globale ed è flessibile al punto che può essere applicata una configurazione con granularità per nodo o come configurazione del ruolo che si estende su più server che devono avere configurazioni identiche.</span><span class="sxs-lookup"><span data-stu-id="53f26-281">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="53f26-282">Identificatori univoci globali (GUID)</span><span class="sxs-lookup"><span data-stu-id="53f26-282">Guids</span></span>

<span data-ttu-id="53f26-283">La pianificazione della configurazione degli identificatori **GUID** richiede ulteriore attenzione nel caso di una distribuzione di server di pull.</span><span class="sxs-lookup"><span data-stu-id="53f26-283">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="53f26-284">Non esistono requisiti specifici su come gestire gli identificatori **GUID** e il processo è probabilmente univoco per ogni ambiente.</span><span class="sxs-lookup"><span data-stu-id="53f26-284">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="53f26-285">Il processo può variare da semplice a complesso, ad esempio un file CSV archiviato centralmente, una semplice tabella SQL, un database CMDB o una soluzione complessa che richiede l'integrazione con un altro strumento o soluzione software.</span><span class="sxs-lookup"><span data-stu-id="53f26-285">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="53f26-286">I processi seguono due approcci generali:</span><span class="sxs-lookup"><span data-stu-id="53f26-286">There are two general approaches:</span></span>

- <span data-ttu-id="53f26-287">**Assegnazione di identificatori GUID per server**: questo approccio garantisce che ogni configurazione del server venga controllata individualmente.</span><span class="sxs-lookup"><span data-stu-id="53f26-287">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="53f26-288">Ciò offre un livello di precisione per gli aggiornamenti e funziona efficientemente in ambienti con pochi server.</span><span class="sxs-lookup"><span data-stu-id="53f26-288">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="53f26-289">**Assegnazione di identificatori GUID per ruolo del server**: tutti i server che eseguono la stessa funzione, ad esempio i server Web, usano lo stesso identificatore GUID come riferimento ai dati di configurazione necessari.</span><span class="sxs-lookup"><span data-stu-id="53f26-289">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span> <span data-ttu-id="53f26-290">Tenere presente che se molti server condividono lo stesso identificatore GUID, tutti i server verranno contemporaneamente aggiornati quando cambia la configurazione.</span><span class="sxs-lookup"><span data-stu-id="53f26-290">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="53f26-291">L'identificatore GUID è un elemento da considerare come informazione sensibile perché potrebbe essere usato a proprio vantaggio da utenti malintenzionati che vogliono conoscere come sono distribuiti e configurati i server nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="53f26-291">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="53f26-292">Per altre informazioni, vedere [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Allocazione sicura degli identificatori GUID nella modalità pull di configurazione dello stato desiderato tramite Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="53f26-292">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="53f26-293">Pianificazione dell'attività</span><span class="sxs-lookup"><span data-stu-id="53f26-293">Planning task</span></span>
- <span data-ttu-id="53f26-294">Chi sarà responsabile per copiare le configurazioni nella cartella del server di pull quando sono pronte?</span><span class="sxs-lookup"><span data-stu-id="53f26-294">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>
- <span data-ttu-id="53f26-295">Se le configurazioni vengono create da un team di applicazione, quale sarà il processo per consegnarle?</span><span class="sxs-lookup"><span data-stu-id="53f26-295">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>
- <span data-ttu-id="53f26-296">Verrà usato un repository per archiviare le configurazioni mentre vengono create, tra i team?</span><span class="sxs-lookup"><span data-stu-id="53f26-296">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>
- <span data-ttu-id="53f26-297">Verrà automatizzato il processo di copia delle configurazione nel server e di creazione di un checksum quando sono pronte?</span><span class="sxs-lookup"><span data-stu-id="53f26-297">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>
- <span data-ttu-id="53f26-298">Come verrà eseguito il mapping degli identificatori GUID ai server o ai ruoli e dove verrà archiviato?</span><span class="sxs-lookup"><span data-stu-id="53f26-298">How will you map Guids to servers or roles, and where will this be stored?</span></span>
- <span data-ttu-id="53f26-299">Quale processo verrà usato per configurare i computer client e come si integrerà con il processo di creazione e archiviazione degli identificatori GUID di configurazione?</span><span class="sxs-lookup"><span data-stu-id="53f26-299">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>

## <a name="installation-guide"></a><span data-ttu-id="53f26-300">Guida all'installazione</span><span class="sxs-lookup"><span data-stu-id="53f26-300">Installation Guide</span></span>

<span data-ttu-id="53f26-301">*Gli script illustrati in questo documento sono esempi stabili. Esaminare sempre gli script con attenzione prima di eseguirli in un ambiente di produzione.*</span><span class="sxs-lookup"><span data-stu-id="53f26-301">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="53f26-302">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="53f26-302">Prerequisites</span></span>

<span data-ttu-id="53f26-303">Per verificare la versione di PowerShell nel server usare il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="53f26-303">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="53f26-304">Se possibile, eseguire l'aggiornamento alla versione più recente di Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="53f26-304">If possible, upgrade to the latest version of Windows Management Framework.</span></span> <span data-ttu-id="53f26-305">Successivamente, scaricare il modulo `xPsDesiredStateConfiguration` con il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="53f26-305">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="53f26-306">Il comando chiederà conferma prima di scaricare il modulo.</span><span class="sxs-lookup"><span data-stu-id="53f26-306">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="53f26-307">Script di installazione e configurazione</span><span class="sxs-lookup"><span data-stu-id="53f26-307">Installation and configuration scripts</span></span>

<span data-ttu-id="53f26-308">Il metodo migliore per distribuire un server di pull DSC è usare uno script di configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-308">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="53f26-309">Questo documento illustra script che includono impostazioni di base per configurare solo il servizio Web DSC e impostazioni avanzate per configurare completamente Windows Server, incluso il servizio Web DSC.</span><span class="sxs-lookup"><span data-stu-id="53f26-309">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="53f26-310">Nota:  attualmente il modulo DSC `xPSDesiredStateConfiguration` richiede che il server sia configurato su impostazioni locali EN-US.</span><span class="sxs-lookup"><span data-stu-id="53f26-310">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="53f26-311">Configurazione di base per Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="53f26-311">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="53f26-312">Configurazione avanzata per Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="53f26-312">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="53f26-313">Verificare la funzionalità del server di pull</span><span class="sxs-lookup"><span data-stu-id="53f26-313">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="53f26-314">Configurare i client</span><span class="sxs-lookup"><span data-stu-id="53f26-314">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="53f26-315">Riferimenti aggiuntivi, frammenti di codice ed esempi</span><span class="sxs-lookup"><span data-stu-id="53f26-315">Additional references, snippets, and examples</span></span>

<span data-ttu-id="53f26-316">Questo esempio illustra come avviare manualmente una connessione client (richiede WMF5) per il test.</span><span class="sxs-lookup"><span data-stu-id="53f26-316">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="53f26-317">Il cmdlet [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) viene usato per aggiungere un tipo di record CNAME a una zona DNS.</span><span class="sxs-lookup"><span data-stu-id="53f26-317">The [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="53f26-318">La funzione di PowerShell per [creare un checksum e pubblicare MOF DSC al Server di Pull SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genera automaticamente il checksum necessario e quindi copia la configurazione MOF e i file di checksum nel server di pull SMB.</span><span class="sxs-lookup"><span data-stu-id="53f26-318">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="53f26-319">Appendice - Informazioni sui tipi di file di dati del servizio ODATA</span><span class="sxs-lookup"><span data-stu-id="53f26-319">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="53f26-320">Un file di dati viene archiviato per creare informazioni durante la distribuzione di un server di pull che include il servizio Web OData.</span><span class="sxs-lookup"><span data-stu-id="53f26-320">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="53f26-321">Il tipo di file dipende dal sistema operativo, come specificato di seguito.</span><span class="sxs-lookup"><span data-stu-id="53f26-321">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="53f26-322">**Windows Server 2012** Il tipo di file sarà sempre MDB</span><span class="sxs-lookup"><span data-stu-id="53f26-322">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="53f26-323">**Windows Server 2012 R2** Il tipo di file predefinito è EDB a meno che non venga specificato un file con estensione MDB nella configurazione</span><span class="sxs-lookup"><span data-stu-id="53f26-323">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="53f26-324">Nello [script di esempio avanzato](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) per installare un server di pull è incluso anche un esempio di come controllare automaticamente le impostazioni del file web.config per evitare qualsiasi possibilità di errore causato dal tipo di file.</span><span class="sxs-lookup"><span data-stu-id="53f26-324">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
