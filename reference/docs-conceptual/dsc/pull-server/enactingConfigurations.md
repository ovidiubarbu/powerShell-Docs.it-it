---
ms.date: 10/16/2017
keywords: dsc,powershell,configurazione,installazione
title: Applicazione delle configurazioni
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953648"
---
# <a name="enacting-configurations"></a><span data-ttu-id="20a6a-103">Applicazione delle configurazioni</span><span class="sxs-lookup"><span data-stu-id="20a6a-103">Enacting configurations</span></span>

><span data-ttu-id="20a6a-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="20a6a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="20a6a-105">Ci sono due modi per applicare le configurazioni di PowerShell DSC (Desired State Configuration): la modalità push e la modalità pull.</span><span class="sxs-lookup"><span data-stu-id="20a6a-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="20a6a-106">Modalità push</span><span class="sxs-lookup"><span data-stu-id="20a6a-106">Push mode</span></span>

<span data-ttu-id="20a6a-107">![Modalità push](../images/pushModel.png "Come funziona la modalità push")</span><span class="sxs-lookup"><span data-stu-id="20a6a-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="20a6a-108">La modalità push fa riferimento a un utente che applica attivamente una configurazione in un nodo di destinazione chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="20a6a-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="20a6a-109">Dopo la creazione e la compilazione di una configurazione, è possibile applicarla in modalità push chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration), impostando il parametro -Path del cmdlet sul percorso in cui si trova il file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="20a6a-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="20a6a-110">Se, ad esempio, il file MOF di configurazione si trova in `C:\DSC\Configurations\localhost.mof`, per applicarlo al computer locale usare il comando seguente: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="20a6a-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="20a6a-111">__Nota__: per impostazione predefinita, DSC esegue una configurazione come processo in background.</span><span class="sxs-lookup"><span data-stu-id="20a6a-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="20a6a-112">Per eseguire la configurazione in modo interattivo, chiamare [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) con il parametro __-Wait__.</span><span class="sxs-lookup"><span data-stu-id="20a6a-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="20a6a-113">Modalità pull</span><span class="sxs-lookup"><span data-stu-id="20a6a-113">Pull mode</span></span>

<span data-ttu-id="20a6a-114">![Modalità pull](../images/pullModel.png "Come funziona la modalità pull")</span><span class="sxs-lookup"><span data-stu-id="20a6a-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="20a6a-115">In modalità pull, i client di pull sono configurati per ottenere le relative configurazioni DSC da un servizio di pull remoto.</span><span class="sxs-lookup"><span data-stu-id="20a6a-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="20a6a-116">Analogamente, il servizio di pull è stato configurato per ospitare il servizio DSC e ne è stato effettuato il provisioning con le configurazioni e le risorse richieste dai client di pull.</span><span class="sxs-lookup"><span data-stu-id="20a6a-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="20a6a-117">Ogni client di pull ha un evento pianificato che esegue un controllo di conformità periodico sulla configurazione del nodo.</span><span class="sxs-lookup"><span data-stu-id="20a6a-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="20a6a-118">Quando l'evento viene generato per la prima volta, Gestione configurazione locale nel client di pull effettua una richiesta al servizio di pull per ottenere la configurazione specificata in Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="20a6a-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="20a6a-119">Se tale configurazione è disponibile nel servizio di pull e supera i controlli di convalida iniziali, viene scaricata nel client di pull, dove viene quindi eseguita da Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="20a6a-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="20a6a-120">Gestione configurazione locale verifica che il client sia conforme alla configurazione a intervalli regolari, come specificato dalla proprietà **ConfigurationModeFrequencyMins** di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="20a6a-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="20a6a-121">Gestione configurazione locale verifica se sono disponibili configurazioni aggiornate nel servizio di pull a intervalli regolari, come specificato dalla proprietà **RefreshModeFrequency** di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="20a6a-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="20a6a-122">Per informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="20a6a-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="20a6a-123">La soluzione consigliata per l'hosting di un servizio di pull è il servizio cloud DSC, ovvero [Automazione di Azure](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="20a6a-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="20a6a-124">Questa soluzione ospitata offre funzionalità di gestione con interfaccia grafica, creazione di report e amministrazione centralizzata.</span><span class="sxs-lookup"><span data-stu-id="20a6a-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="20a6a-125">Per altre informazioni sulla configurazione di un servizio di pull in Windows Server, vedere [Configurazione di un server di pull Web DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="20a6a-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="20a6a-126">Tenere presente, tuttavia, che questa implementazione offre funzionalità limitate e richiede alcuni interventi di integrazione manuali.</span><span class="sxs-lookup"><span data-stu-id="20a6a-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="20a6a-127">Gli argomenti seguenti illustrano il servizio e i client di pull:</span><span class="sxs-lookup"><span data-stu-id="20a6a-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="20a6a-128">Panoramica della piattaforma DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="20a6a-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="20a6a-129">Configurazione di un server di pull SMB</span><span class="sxs-lookup"><span data-stu-id="20a6a-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="20a6a-130">Configurazione di un client di pull</span><span class="sxs-lookup"><span data-stu-id="20a6a-130">Configuring a pull client</span></span>](pullClientConfigID.md)
