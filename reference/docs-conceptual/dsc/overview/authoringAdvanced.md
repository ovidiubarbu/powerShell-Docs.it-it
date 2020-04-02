---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Informazioni sul ruolo di DSC in una pipeline CI/CD
ms.openlocfilehash: 8d7244a6e5e2c215d9d3ada959b716df2cce0b83
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500817"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="dde2a-103">Informazioni sul ruolo di DSC in una pipeline CI/CD</span><span class="sxs-lookup"><span data-stu-id="dde2a-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="dde2a-104">Questo articolo descrive i tipi di approcci disponibili per la combinazione di configurazioni e risorse.</span><span class="sxs-lookup"><span data-stu-id="dde2a-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="dde2a-105">L'obiettivo per ogni scenario è lo stesso: ridurre la complessità quando sono preferibili più configurazioni per raggiungere uno stato finale della distribuzione del server.</span><span class="sxs-lookup"><span data-stu-id="dde2a-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span> <span data-ttu-id="dde2a-106">Ad esempio, si possono avere più team che contribuiscono al risultato di una distribuzione di server, da un lato il proprietario dell'applicazione che gestisce lo stato dell'applicazione e dall'altro un team centrale che rilascia le modifiche per le baseline della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="dde2a-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span> <span data-ttu-id="dde2a-107">Di seguito sono descritte in dettaglio le caratteristiche di ogni approccio con i relativi vantaggi e rischi.</span><span class="sxs-lookup"><span data-stu-id="dde2a-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pipeline](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="dde2a-109">Tipi di tecniche di creazione e modifica in collaborazione</span><span class="sxs-lookup"><span data-stu-id="dde2a-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="dde2a-110">Esistono due soluzioni integrate in Gestione configurazione locale per abilitare questo concetto:</span><span class="sxs-lookup"><span data-stu-id="dde2a-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

|        <span data-ttu-id="dde2a-111">Concetto</span><span class="sxs-lookup"><span data-stu-id="dde2a-111">Concept</span></span>         |                    <span data-ttu-id="dde2a-112">Informazioni dettagliate</span><span class="sxs-lookup"><span data-stu-id="dde2a-112">Detailed Information</span></span>                     |
| ---------------------- | ----------------------------------------------------------- |
| <span data-ttu-id="dde2a-113">Configurazioni parziali</span><span class="sxs-lookup"><span data-stu-id="dde2a-113">Partial Configurations</span></span> | [<span data-ttu-id="dde2a-114">Documentazione</span><span class="sxs-lookup"><span data-stu-id="dde2a-114">Documentation</span></span>](../pull-server/partialConfigs.md)           |
| <span data-ttu-id="dde2a-115">Risorse composite</span><span class="sxs-lookup"><span data-stu-id="dde2a-115">Composite Resources</span></span>    | [<span data-ttu-id="dde2a-116">Documentazione</span><span class="sxs-lookup"><span data-stu-id="dde2a-116">Documentation</span></span>](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="dde2a-117">Informazioni sull'impatto di ogni approccio</span><span class="sxs-lookup"><span data-stu-id="dde2a-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="dde2a-118">Ognuna di queste soluzioni può essere usata per gestire il risultato di una distribuzione di server.</span><span class="sxs-lookup"><span data-stu-id="dde2a-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span> <span data-ttu-id="dde2a-119">Tuttavia, vi è una differenza significativa in termini di impatto tra i vari approcci.</span><span class="sxs-lookup"><span data-stu-id="dde2a-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="dde2a-120">Configurazioni parziali</span><span class="sxs-lookup"><span data-stu-id="dde2a-120">Partial Configurations</span></span>

<span data-ttu-id="dde2a-121">Quando si usano configurazioni parziali, la gestione della configurazione locale è configurata in modo da gestire più configurazioni in modo indipendente.</span><span class="sxs-lookup"><span data-stu-id="dde2a-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span> <span data-ttu-id="dde2a-122">Le configurazioni vengono compilate in modo indipendente e quindi assegnate al nodo.</span><span class="sxs-lookup"><span data-stu-id="dde2a-122">Configurations are compiled independently and then assigned to the node.</span></span> <span data-ttu-id="dde2a-123">Questa operazione richiede che la gestione della configurazione locale venga configurata in anticipo con il nome di ogni configurazione.</span><span class="sxs-lookup"><span data-stu-id="dde2a-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](media/authoringAdvanced/PartialConfiguration.jpg)

<span data-ttu-id="dde2a-125">Le configurazioni parziali consentono a due o più team di controllare completamente la configurazione di un server, spesso senza il vantaggio della comunicazione o collaborazione.</span><span class="sxs-lookup"><span data-stu-id="dde2a-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="dde2a-126">I clienti hanno indicato nei propri commenti che questo può causare conflitti tra le risorse, override accidentali e in definitiva la perdita del controllo reale della configurazione dell'asset.</span><span class="sxs-lookup"><span data-stu-id="dde2a-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="dde2a-127">I clienti hanno inoltre indicato che, usando questo modello, le modifiche apportate alla configurazione dai team di gestione probabilmente non vengono completamente testate attraverso una pipeline di rilascio, con risultati imprevisti nell'ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="dde2a-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="dde2a-128">**È essenziale che sia usata una singola pipeline per valutare tutte le modifiche rilasciate ai server.**</span><span class="sxs-lookup"><span data-stu-id="dde2a-128">**It is critical that a single pipeline be used to evaluate all changes released to servers.**</span></span>

<span data-ttu-id="dde2a-129">Nell'illustrazione seguente il Team B rilascia la propria configurazione parziale al Team A. Il Team A esegue i propri test su un server applicando entrambe le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="dde2a-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span> <span data-ttu-id="dde2a-130">In questo modello solo un'autorità è autorizzata ad apportare modifiche nell'ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="dde2a-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

<span data-ttu-id="dde2a-132">Quando il Team B richiede delle modifiche, deve inviare una richiesta pull per l'ambiente di controllo del codice sorgente del Team A.</span><span class="sxs-lookup"><span data-stu-id="dde2a-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span> <span data-ttu-id="dde2a-133">Il Team A esamina le modifiche usando l'automazione dei test e rilascia la configurazione alla produzione quando è certo che le modifiche non causano errori nelle applicazioni o nei servizi ospitati dal server.</span><span class="sxs-lookup"><span data-stu-id="dde2a-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="dde2a-134">Risorse composite</span><span class="sxs-lookup"><span data-stu-id="dde2a-134">Composite Resources</span></span>

<span data-ttu-id="dde2a-135">Una risorsa composita è semplicemente una configurazione DSC inserita in un pacchetto come risorsa.</span><span class="sxs-lookup"><span data-stu-id="dde2a-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span> <span data-ttu-id="dde2a-136">Non sono previsti requisiti speciali per configurare Gestione configurazione locale in modo che accetti le risorse composite.</span><span class="sxs-lookup"><span data-stu-id="dde2a-136">There are no special requirements for configuring LCM to accept composite resources.</span></span> <span data-ttu-id="dde2a-137">Le risorse vengono usate all'interno di una nuova configurazione e un'unica compilazione produce un file MOF.</span><span class="sxs-lookup"><span data-stu-id="dde2a-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](media/authoringAdvanced/CompositeResource.jpg)

<span data-ttu-id="dde2a-139">Esistono due scenari comuni per le risorse composite.</span><span class="sxs-lookup"><span data-stu-id="dde2a-139">There are two common scenarios for composite resources.</span></span> <span data-ttu-id="dde2a-140">Il primo consiste nel ridurre la complessità e astrarre concetti univoci.</span><span class="sxs-lookup"><span data-stu-id="dde2a-140">The first is to reduce complexity and abstract unique concepts.</span></span> <span data-ttu-id="dde2a-141">Il secondo consiste nel consentire l'inserimento in pacchetti delle baseline per un team dell'applicazione per distribuire in modo sicuro alla produzione attraverso la pipeline di rilascio dopo aver superato tutti i test.</span><span class="sxs-lookup"><span data-stu-id="dde2a-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

<span data-ttu-id="dde2a-142">Le risorse composite alzano di livello sia la composizione che la collaborazione usando una pipeline e creando maturità operativa.</span><span class="sxs-lookup"><span data-stu-id="dde2a-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity.</span></span>

<span data-ttu-id="dde2a-143">È possibile che l'utente stia già usando le risorse composite senza saperlo.</span><span class="sxs-lookup"><span data-stu-id="dde2a-143">You might be already using composite resources without realizing it.</span></span> <span data-ttu-id="dde2a-144">Un esempio è **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="dde2a-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="dde2a-145">Questa risorsa gestisce lo stato di più servizi Windows senza indicarli singolarmente.</span><span class="sxs-lookup"><span data-stu-id="dde2a-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span> <span data-ttu-id="dde2a-146">La proprietà Name accetta una matrice di stringhe per specificare il nome di ogni servizio.</span><span class="sxs-lookup"><span data-stu-id="dde2a-146">The Name property accepts an array of strings to provide the name of each service.</span></span> <span data-ttu-id="dde2a-147">Quando viene compilata la configurazione, il file MOF contiene una sezione Service univoca per ogni nome passato a ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="dde2a-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="dde2a-148">Le organizzazioni possono avere "agenti" o "middleware" che devono essere installati in ogni server.</span><span class="sxs-lookup"><span data-stu-id="dde2a-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span> <span data-ttu-id="dde2a-149">Una risorsa composita è l'approccio migliore per gestire le dipendenze, l'installazione e la configurazione di tali strumenti e utilità.</span><span class="sxs-lookup"><span data-stu-id="dde2a-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="dde2a-150">La persona o il team responsabile delle soluzioni che si estendono su più server crea una configurazione che contiene i requisiti.</span><span class="sxs-lookup"><span data-stu-id="dde2a-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span> <span data-ttu-id="dde2a-151">Successivamente, la configurazione viene compressa come risorsa composita seguendo le istruzioni contenute nella documentazione della risorsa composita.</span><span class="sxs-lookup"><span data-stu-id="dde2a-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span> <span data-ttu-id="dde2a-152">Infine, la nuova risorsa composita deve essere pubblicata in un percorso, ad esempio una condivisione file o un feed NuGet in cui i team dell'applicazione possano usarla per le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="dde2a-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="dde2a-153">Ogni volta che il team rilascia una nuova versione, incrementa il numero di versione nel manifesto del modulo per la risorsa composita.</span><span class="sxs-lookup"><span data-stu-id="dde2a-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span> <span data-ttu-id="dde2a-154">I team dell'applicazione includono la risorsa composita nella configurazione che creano per la gestione delle dipendenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="dde2a-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span> <span data-ttu-id="dde2a-155">Quando i team addetti a operazioni e sicurezza rilasciano una nuova versione della propria risorsa, informano i team dell'applicazione che è stata apportata una nuova modifica.</span><span class="sxs-lookup"><span data-stu-id="dde2a-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="dde2a-156">I team dell'applicazione possono attivare un rilascio alla produzione in cui l'unica modifica è apportata alle baseline.</span><span class="sxs-lookup"><span data-stu-id="dde2a-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="dde2a-157">Tuttavia, questo offre la possibilità di valutare l'impatto sulle applicazioni prima di rischiare un'interruzione del servizio.</span><span class="sxs-lookup"><span data-stu-id="dde2a-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

> [!NOTE]
> <span data-ttu-id="dde2a-158">Il feedback relativo all'uso delle risorse composite include anche critiche per il fatto che apportare modifiche richiede la compilazione e il rilascio di un nuovo file MOF.</span><span class="sxs-lookup"><span data-stu-id="dde2a-158">Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span> <span data-ttu-id="dde2a-159">Questo si verifica per motivi strutturali.</span><span class="sxs-lookup"><span data-stu-id="dde2a-159">This is by design.</span></span> <span data-ttu-id="dde2a-160">Ogni nuova versione della configurazione deve includere un riferimento statico a una versione specifica di ogni risorsa e deve essere convalidata dai test prima di raggiungere i nodi del server di produzione.</span><span class="sxs-lookup"><span data-stu-id="dde2a-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span> <span data-ttu-id="dde2a-161">Il processo di test e rilascio delle modifiche dal controllo del codice sorgente consente di creare un ambiente sicuro per il rilascio delle modifiche in batch di piccole dimensioni ma frequenti.</span><span class="sxs-lookup"><span data-stu-id="dde2a-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="dde2a-162">Per altre informazioni sull'uso di pipeline di versione per gestire l'infrastruttura di base, vedere il white paper: [The Release Pipeline Model](../further-reading/whitepapers.md) (Il modello della pipeline di versione).</span><span class="sxs-lookup"><span data-stu-id="dde2a-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
