---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a PowerShell DSC (Desired State Configuration)
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189721"
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="f7faf-103">Introduzione a PowerShell DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="f7faf-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="f7faf-104">Questa guida descrive come iniziare a creare documenti di PowerShell DSC (Desired State Configuration) e applicarli ai computer.</span><span class="sxs-lookup"><span data-stu-id="f7faf-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="f7faf-105">Si presuppone una familiarità di base con i cmdlet, i moduli e le funzioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7faf-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="f7faf-106">Creare una configurazione</span><span class="sxs-lookup"><span data-stu-id="f7faf-106">Create a Configuration</span></span> ##

<span data-ttu-id="f7faf-107">Le [**configurazioni**](https://msdn.microsoft.com/powershell/dsc/configurations) sono documenti che descrivono un ambiente.</span><span class="sxs-lookup"><span data-stu-id="f7faf-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="f7faf-108">Gli ambienti sono costituiti da "**nodi**", che sono in genere macchine virtuali o computer fisici.</span><span class="sxs-lookup"><span data-stu-id="f7faf-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="f7faf-109">Le configurazioni possono avere svariate forme.</span><span class="sxs-lookup"><span data-stu-id="f7faf-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="f7faf-110">Il metodo più semplice per creare una nuova configurazione consiste nel creare un file PS1 (script di PowerShell).</span><span class="sxs-lookup"><span data-stu-id="f7faf-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="f7faf-111">A questo scopo, aprire l'editor preferito.</span><span class="sxs-lookup"><span data-stu-id="f7faf-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="f7faf-112">PowerShell ISE è un'ottima scelta, perché riconosce DSC in modo nativo.</span><span class="sxs-lookup"><span data-stu-id="f7faf-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="f7faf-113">Salvare il codice seguente come file PS1:</span><span class="sxs-lookup"><span data-stu-id="f7faf-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="f7faf-114">Parti di una configurazione</span><span class="sxs-lookup"><span data-stu-id="f7faf-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="f7faf-115">**Configuration** è una parola chiave che è stata aggiunta in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f7faf-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="f7faf-116">Significa un tipo speciale di funzione di PowerShell usata da DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="f7faf-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="f7faf-117">In questo esempio la funzione si chiama myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="f7faf-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="f7faf-118">La riga successiva è un'istruzione di importazione, simile all'importazione di un modulo.</span><span class="sxs-lookup"><span data-stu-id="f7faf-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="f7faf-119">Questa riga verrà descritta più avanti.</span><span class="sxs-lookup"><span data-stu-id="f7faf-119">It will be discussed later on.</span></span>

<span data-ttu-id="f7faf-120">Il termine "nodo" definisce il nome del computer su cui agirà questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="f7faf-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="f7faf-121">Benché questa configurazione venga modificata in locale, le configurazioni possono raggiungere nodi remoti e configurarli.</span><span class="sxs-lookup"><span data-stu-id="f7faf-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="f7faf-122">I nodi possono essere nomi di computer o indirizzi IP.</span><span class="sxs-lookup"><span data-stu-id="f7faf-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="f7faf-123">Un singolo documento di configurazione può contenere più nodi.</span><span class="sxs-lookup"><span data-stu-id="f7faf-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="f7faf-124">Usando [dati di configurazione](https://msdn.microsoft.com/powershell/dsc/configdata), è possibile fare in modo che la stessa configurazione venga applicata a più nodi.</span><span class="sxs-lookup"><span data-stu-id="f7faf-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="f7faf-125">In questo caso il nodo è "localhost", ovvero il computer locale.</span><span class="sxs-lookup"><span data-stu-id="f7faf-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="f7faf-126">L'elemento successivo è una [**risorsa**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="f7faf-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="f7faf-127">Le risorse sono blocchi predefiniti di configurazioni.</span><span class="sxs-lookup"><span data-stu-id="f7faf-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="f7faf-128">Ogni risorsa è un modulo che definisce la logica di implementazione di un singolo aspetto di un computer.</span><span class="sxs-lookup"><span data-stu-id="f7faf-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="f7faf-129">È possibile visualizzare ogni risorsa nel computer eseguendo **Get-DscResource** in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7faf-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="f7faf-130">Le risorse devono essere presenti nel computer locale e prima di poter essere usate in una configurazione devono essere importate con **Import-DscResource**, che si trova nella seconda riga di questa configurazione.</span><span class="sxs-lookup"><span data-stu-id="f7faf-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="f7faf-131">**Applicazione di una configurazione**</span><span class="sxs-lookup"><span data-stu-id="f7faf-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="f7faf-132">Se lo script sopra viene salvato ed eseguito, non viene prodotto alcun output.</span><span class="sxs-lookup"><span data-stu-id="f7faf-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="f7faf-133">Il motivo è che una configurazione è solo una funzione e lo script sopra ha definito la funzione, ma senza eseguirla.</span><span class="sxs-lookup"><span data-stu-id="f7faf-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="f7faf-134">Dopo che la funzione è stata definita, deve essere richiamata:</span><span class="sxs-lookup"><span data-stu-id="f7faf-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="f7faf-135">Quando vengono eseguite, le funzioni di configurazione verificano la validità della configurazione.</span><span class="sxs-lookup"><span data-stu-id="f7faf-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="f7faf-136">La configurazione non deve includere errori di sintassi, per le risorse devono essere definiti tutti i parametri obbligatori e tutte le risorse devono essere importate prima dell'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f7faf-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="f7faf-137">Quando la configurazione viene eseguita, crea una cartella con il nome della configurazione stessa che contiene un **file MOF** per ogni nodo nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="f7faf-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="f7faf-138">Il file MOF è un formato di gestione basato sugli standard usato da PowerShell DSC per comunicare in rete.</span><span class="sxs-lookup"><span data-stu-id="f7faf-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="f7faf-139">Per applicare la configurazione:</span><span class="sxs-lookup"><span data-stu-id="f7faf-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="f7faf-140">Viene creato un processo di PowerShell che raggiunge i nodi nella configurazione e li configura.</span><span class="sxs-lookup"><span data-stu-id="f7faf-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="f7faf-141">Per visualizzare l'output del processo, usare -Wait.</span><span class="sxs-lookup"><span data-stu-id="f7faf-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```