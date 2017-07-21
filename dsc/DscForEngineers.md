---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Panoramica di DSC (Desired State Configuration) per decision maker
ms.openlocfilehash: 50aaa407e02b8466a7df909711454e88b07c5c1f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="87394-103">Panoramica di DSC (Desired State Configuration) per tecnici</span><span class="sxs-lookup"><span data-stu-id="87394-103">Desired State Configuration Overview for Engineers</span></span> #

<span data-ttu-id="87394-104">In questo documento è destinato ai team di sviluppatori e tecnici operativi per illustrare i vantaggi di PowerShell DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="87394-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="87394-105">Per una panoramica di più alto livello del valore offerto da DSC, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="87394-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="87394-106">Vantaggi dell'uso di DSC</span><span class="sxs-lookup"><span data-stu-id="87394-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="87394-107">DSC offre i vantaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="87394-107">DSC exists to:</span></span>
- <span data-ttu-id="87394-108">Ridurre la complessità dello scripting in Windows</span><span class="sxs-lookup"><span data-stu-id="87394-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="87394-109">Aumentare la velocità di iterazione</span><span class="sxs-lookup"><span data-stu-id="87394-109">Increase the speed of iteration</span></span>

<span data-ttu-id="87394-110">Il concetto di "distribuzione continua" è sempre più importante.</span><span class="sxs-lookup"><span data-stu-id="87394-110">The concept of "continuous deployment" is becoming more important.</span></span> <span data-ttu-id="87394-111">La distribuzione continua implica la possibilità di distribuire in modo frequente, potenzialmente più volte al giorno.</span><span class="sxs-lookup"><span data-stu-id="87394-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="87394-112">Lo scopo di queste distribuzioni non è quello di correggere un problema, ma di pubblicare funzionalità in tempi brevi.</span><span class="sxs-lookup"><span data-stu-id="87394-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="87394-113">Permettendo alle nuove funzionalità di passare dalla fase di sviluppo a quella operativa nel modo più rapido e affidabile possibile, si accelera il time-to-value della nuova logica di business.</span><span class="sxs-lookup"><span data-stu-id="87394-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="87394-114">Questa necessità di aggiornamento rapido è esasperata da due tendenze.</span><span class="sxs-lookup"><span data-stu-id="87394-114">There are two trends at play which exacerbate this need to move quickly.</span></span> <span data-ttu-id="87394-115">Il passaggio al cloud computing implica cambiamenti rapidi su larga scala, con un rischio costante di errore.</span><span class="sxs-lookup"><span data-stu-id="87394-115">The move towards cloud computing implies rapid change, at scale, with a constant threat of failure.</span></span>
<span data-ttu-id="87394-116">In questa ottica, per restare al passo è indispensabile adottare soluzioni di automazione.</span><span class="sxs-lookup"><span data-stu-id="87394-116">These implications force automation in order to keep up.</span></span>
<span data-ttu-id="87394-117">Lo sviluppo della mentalità "DevOps" fornisce una valida risposta a questi cambiamenti.</span><span class="sxs-lookup"><span data-stu-id="87394-117">The creation of the "DevOps" mentality is a response to these changes.</span></span> 


<span data-ttu-id="87394-118">DSC è una piattaforma che offre funzionalità di distribuzione, configurazione e conformità dichiarative, autonome e idempotenti (ripetibili).</span><span class="sxs-lookup"><span data-stu-id="87394-118">DSC is a platform that provides declarative, autonomous and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="87394-119">La piattaforma DSC consente di verificare che i componenti del data center siano configurati correttamente, in modo da evitare errori e impedire costosi problemi di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="87394-119">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="87394-120">Trattando le configurazioni DSC come parte del codice dell'applicazione, DSC consente la distribuzione continua.</span><span class="sxs-lookup"><span data-stu-id="87394-120">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="87394-121">La configurazione DSC deve essere aggiornata come parte dell'applicazione, assicurando così che le informazioni necessarie per distribuire l'applicazione siano sempre aggiornate e pronte per l'uso.</span><span class="sxs-lookup"><span data-stu-id="87394-121">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>


## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="87394-122">"Se si ha PowerShell, perché è necessario usare anche Desired State Configuration?"</span><span class="sxs-lookup"><span data-stu-id="87394-122">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="87394-123">Le configurazioni DSC fanno distinzione tra l'intenzione, ossia "l'operazione che si vuole eseguire", e l'esecuzione, ossia "il modo in cui eseguire tale operazione".</span><span class="sxs-lookup"><span data-stu-id="87394-123">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="87394-124">Ciò significa che la logica di esecuzione è contenuta all'interno delle risorse.</span><span class="sxs-lookup"><span data-stu-id="87394-124">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="87394-125">Gli utenti non devono sapere come implementare o distribuire una funzionalità quando è disponibile una risorsa DSC per tale funzionalità.</span><span class="sxs-lookup"><span data-stu-id="87394-125">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="87394-126">In questo modo, gli utenti possono concentrarsi sulla struttura della loro distribuzione.</span><span class="sxs-lookup"><span data-stu-id="87394-126">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="87394-127">Ad esempio, gli script di PowerShell dovrebbero avere un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="87394-127">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="87394-128">Questo script è semplice e immediatamente comprensibile.</span><span class="sxs-lookup"><span data-stu-id="87394-128">This script is simple, comprehensible, and straightforward.</span></span> <span data-ttu-id="87394-129">Se tuttavia si prova a trasferirlo nell'ambiente di produzione, possono verificarsi diversi problemi.</span><span class="sxs-lookup"><span data-stu-id="87394-129">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="87394-130">Cosa accade se lo script viene eseguito due volte di seguito?</span><span class="sxs-lookup"><span data-stu-id="87394-130">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="87394-131">E se un utente aveva l'accesso completo alla condivisione?</span><span class="sxs-lookup"><span data-stu-id="87394-131">What happens if Bob previously had Full Access to the share?</span></span> 

<span data-ttu-id="87394-132">Per ovviare a questi problemi, una versione "reale" dello script avrà un aspetto più vicino al seguente:</span><span class="sxs-lookup"><span data-stu-id="87394-132">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="87394-133">Questo script è più complesso, con molte istruzioni per la gestione della logica e degli errori.</span><span class="sxs-lookup"><span data-stu-id="87394-133">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="87394-134">Lo script è più complesso perché non indica più le operazioni da eseguire, ma *in che modo eseguirle*.</span><span class="sxs-lookup"><span data-stu-id="87394-134">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="87394-135">DSC consente di specificare le operazioni da eseguire ed è in grado di astrarre la logica sottostante.</span><span class="sxs-lookup"><span data-stu-id="87394-135">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present" 
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"  
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
} 
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="87394-136">Questo script è formattato correttamente ed è facilmente leggibile.</span><span class="sxs-lookup"><span data-stu-id="87394-136">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="87394-137">I percorsi di logica e i criteri di gestione degli errori sono ancora presenti nell'implementazione della [risorsa](resources.md), ma non sono visibili all'autore dello script.</span><span class="sxs-lookup"><span data-stu-id="87394-137">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span> 



## <a name="separating-environment-from-structure"></a><span data-ttu-id="87394-138">Separazione dell'ambiente dalla struttura</span><span class="sxs-lookup"><span data-stu-id="87394-138">Separating Environment from Structure</span></span>

<span data-ttu-id="87394-139">Un modello comune in DevOps consiste nella presenza di più ambienti per la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="87394-139">A common pattern in DevOps is to have multiple environments for deployment.</span></span> <span data-ttu-id="87394-140">Ad esempio, può essere presente un ambiente di sviluppo che consente di creare rapidamente prototipi di nuovo codice.</span><span class="sxs-lookup"><span data-stu-id="87394-140">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="87394-141">Il codice dell'ambiente di sviluppo viene trasferito in un ambiente di test, in cui altri utenti verificano la nuova funzionalità.</span><span class="sxs-lookup"><span data-stu-id="87394-141">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="87394-142">Infine, il codice passa all'ambiente di produzione, ossia all'ambiente del sito attivo.</span><span class="sxs-lookup"><span data-stu-id="87394-142">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="87394-143">Le configurazioni DSC consentono questa pipeline sviluppo-test-produzione tramite l'uso di [dati di configurazione](configData.md).</span><span class="sxs-lookup"><span data-stu-id="87394-143">DSC configurations accomodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="87394-144">Questa caratteristica ha l'effetto di astrarre maggiormente la differenza tra la struttura della configurazione e i nodi gestiti.</span><span class="sxs-lookup"><span data-stu-id="87394-144">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="87394-145">È ad esempio possibile definire una configurazione che richiede un server SQL, un server IIS e un server di livello intermedio.</span><span class="sxs-lookup"><span data-stu-id="87394-145">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span> <span data-ttu-id="87394-146">Indipendentemente dai nodi che ricevono le diverse parti della configurazione, questi tre elementi saranno sempre presenti.</span><span class="sxs-lookup"><span data-stu-id="87394-146">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="87394-147">È possibile usare i dati di configurazione per far puntare tutti e tre gli elementi allo stesso computer per un ambiente di sviluppo, separare i tre elementi su tre computer diversi per un ambiente di test e infine farli puntare a tutti i server di produzione per l'ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="87394-147">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="87394-148">Per la distribuzione nei diversi ambienti, è possibile richiamare `Start-DscConfiguration` con i dati di configurazione corretti per l'ambiente di destinazione.</span><span class="sxs-lookup"><span data-stu-id="87394-148">To deploy to the different environments, you can invoke `Start-DscConfiguration` with the correct configuration data for the environment you want to target.</span></span> 

## <a name="see-also"></a><span data-ttu-id="87394-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="87394-149">See Also</span></span>

[<span data-ttu-id="87394-150">Configurazioni</span><span class="sxs-lookup"><span data-stu-id="87394-150">Configurations</span></span>](configurations.md)

[<span data-ttu-id="87394-151">Dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="87394-151">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="87394-152">Risorse</span><span class="sxs-lookup"><span data-stu-id="87394-152">Resources</span></span>](resources.md)

