---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: 8c325ce1c665181cff646eef6c5e7d55e9081e5e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="15ef0-103">Stato di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="15ef0-103">PowerShell Gallery Status</span></span>
=========================
## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="15ef0-104">01/06/2017 - Distribuzione in Automazione di Azure attualmente non disponibile</span><span class="sxs-lookup"><span data-stu-id="15ef0-104">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="15ef0-105">__Riepilogo dell'impatto__: la distribuzione di elementi con dipendenze in Automazione di Azure da PowerShell Gallery non è attualmente disponibile.</span><span class="sxs-lookup"><span data-stu-id="15ef0-105">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="15ef0-106">L'importazione di elementi da PowerShell Gallery dall'interno di Automazione di Azure è ancora disponibile.</span><span class="sxs-lookup"><span data-stu-id="15ef0-106">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="15ef0-107">__Causa radice__: gli elementi con dipendenze che sono stati distribuiti in precedenza in Automazione di Azure non verranno distribuiti in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="15ef0-107">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="15ef0-108">I tecnici hanno identificato un problema nella modalità in cui i modelli ARM vengono generati per gli elementi con dipendenze per la funzionalità di distribuzione in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="15ef0-108">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="15ef0-109">__Risoluzione__: i tecnici stanno lavorando per risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="15ef0-109">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="15ef0-110">La soluzione corrente per gli utenti consiste nell'importare l'elemento da PowerShell Gallery dall'interno di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="15ef0-110">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="15ef0-111">__Passaggi successivi__: i tecnici risolveranno il problema a breve.</span><span class="sxs-lookup"><span data-stu-id="15ef0-111">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="15ef0-112">Nel frattempo, usare la soluzione consigliata.</span><span class="sxs-lookup"><span data-stu-id="15ef0-112">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="15ef0-113">11/04/2017 - Gli utenti non possono accedere con account Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="15ef0-113">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="15ef0-114">__Riepilogo del problema__: alcuni utenti non sono in grado di accedere a PowerShell Gallery usando gli account Azure AD.</span><span class="sxs-lookup"><span data-stu-id="15ef0-114">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="15ef0-115">__Causa radice__: durante un aggiornamento per un'iterazione più sicura con AAD, non è stata eseguita una modifica delle impostazioni.</span><span class="sxs-lookup"><span data-stu-id="15ef0-115">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="15ef0-116">Poiché i test eseguiti per convalidare la modifica non includevano determinati tipi di account AAD, la distribuzione è stata eseguita.</span><span class="sxs-lookup"><span data-stu-id="15ef0-116">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="15ef0-117">__Risoluzione__: I tecnici hanno identificato l'impostazione mancante e corretto il problema.</span><span class="sxs-lookup"><span data-stu-id="15ef0-117">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="15ef0-118">__Passaggi successivi__: verranno modificati i test per includere un set più ampio di tipi di account AAD.</span><span class="sxs-lookup"><span data-stu-id="15ef0-118">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="15ef0-119">27/03/2017 - RISOLTO: impossibile visualizzare singole pagine di moduli e script</span><span class="sxs-lookup"><span data-stu-id="15ef0-119">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="15ef0-120">__Riepilogo del problema__: i collegamenti diretti alle singole pagine di moduli e script in https://www.powershellgallery.com erano interrotti.</span><span class="sxs-lookup"><span data-stu-id="15ef0-120">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="15ef0-121">Il problema era segnalato in tutte le aree.</span><span class="sxs-lookup"><span data-stu-id="15ef0-121">This was being reported across all the regions.</span></span> <span data-ttu-id="15ef0-122">Il problema non influiva sui cmdlet di PowerShellGet, ovvero Install-Module, Install-Script, Update-Module, Update-Script e Publish-Module. Publish-Script continuava a funzionare.</span><span class="sxs-lookup"><span data-stu-id="15ef0-122">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="15ef0-123">__Causa radice__: i tecnici hanno identificato la causa in un problema di visualizzazione dei pulsanti per i social media come Facebook nella pagina.</span><span class="sxs-lookup"><span data-stu-id="15ef0-123">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="15ef0-124">__Risoluzione__: tecnici hanno risolto il problema disabilitando le informazioni sul conteggio di Facebook.</span><span class="sxs-lookup"><span data-stu-id="15ef0-124">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="15ef0-125">__Passaggi successivi__: è stato aperto un problema di rilevamento interno per correggere l'uso dell'API di Facebook.</span><span class="sxs-lookup"><span data-stu-id="15ef0-125">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="15ef0-126">15/12/2016 - Impossibile inviare messaggi di posta elettronica tramite il sito Web PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="15ef0-126">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="15ef0-127">__Riepilogo del problema__: tra il 13/12/2016 e il 15/12/2016, tutti i messaggi inviati tramite Contact Owners, Manage Owners, Contact Support o Report Abuse non sono stati ricevuti dagli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="15ef0-127">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="15ef0-128">__Causa radice__: i tecnici hanno identificato la causa in un problema di autenticazione con il server SMTP.</span><span class="sxs-lookup"><span data-stu-id="15ef0-128">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="15ef0-129">__Risoluzione__: i tecnici sono stati in grado di risolvere il problema di autenticazione e ripristinare la connessione al server SMTP.</span><span class="sxs-lookup"><span data-stu-id="15ef0-129">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="15ef0-130">__Passaggi successivi__: se il messaggio di posta elettronica è stato inviato a cgadmin@microsoft.com tramite i collegamenti Contact Owners, Manage Owners, Contact Support o Report Abuse durante questo periodo e non è stata ricevuta alcuna risposta, si prega di rinviare il messaggio.</span><span class="sxs-lookup"><span data-stu-id="15ef0-130">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="15ef0-131">Il team si scusa per l'inconveniente.</span><span class="sxs-lookup"><span data-stu-id="15ef0-131">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="15ef0-132">10/08/2016 - risolto: Impossibile inviare messaggi di posta elettronica a cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="15ef0-132">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="15ef0-133">__Riepilogo del problema__: tra il 05/08/2016 e il 10/08/2016 i clienti non hanno potuto inviare messaggi di posta elettronica a cgadmin@microsoft.com o usare la funzionalità Contattaci.</span><span class="sxs-lookup"><span data-stu-id="15ef0-133">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="15ef0-134">__Causa radice__: i tecnici hanno individuato la causa in una modifica della configurazione dell'account di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="15ef0-134">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="15ef0-135">__Risoluzione__: i tecnici hanno lavorato per risolvere il problema di configurazione.</span><span class="sxs-lookup"><span data-stu-id="15ef0-135">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="15ef0-136">__Passaggi successivi__: se in questo periodo è stato usato il collegamento Contattaci o si è inviato un messaggio a cgadmin@microsoft.com senza ricevere risposta, riprovare.</span><span class="sxs-lookup"><span data-stu-id="15ef0-136">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="15ef0-137">Grazie per la pazienza dimostrata.</span><span class="sxs-lookup"><span data-stu-id="15ef0-137">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="15ef0-138">13/07/2016 - download di elementi non riuscito</span><span class="sxs-lookup"><span data-stu-id="15ef0-138">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="15ef0-139">__Riepilogo dell'impatto__: tra l'11/07/2016 e il 13/07/2016, alcuni clienti hanno incontrato problemi di download degli elementi da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="15ef0-139">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="15ef0-140">Il problema si è probabilmente manifestato nei seguenti messaggi di errore restituiti da Install-Module/Install-Script e Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="15ef0-140">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="15ef0-141">__Causa radice preliminare__: i tecnici hanno individuato un problema con la Rete di distribuzione dei contenuti (CDN) di Azure, che è stata distribuita a PowerShell Gallery l'11/07/2016.</span><span class="sxs-lookup"><span data-stu-id="15ef0-141">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="15ef0-142">__Prevenzione__: i tecnici hanno disabilitato la CDN di Azure in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="15ef0-142">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="15ef0-143">__Passaggi successivi__: ricercare la causa principale sottostante e sviluppare una soluzione per evitare che questo problema si ripresenti in futuro.</span><span class="sxs-lookup"><span data-stu-id="15ef0-143">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="15ef0-144">19/05/2016 - download di elementi non riuscito</span><span class="sxs-lookup"><span data-stu-id="15ef0-144">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="15ef0-145">__Riepilogo dell'impatto__: tra il 17/05/2016 e il 19/05/2016, alcuni clienti hanno incontrato problemi di download degli elementi da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="15ef0-145">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="15ef0-146">Il problema si è probabilmente manifestato nei seguenti messaggi di errore restituiti da Install-Module/Install-Script e Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="15ef0-146">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```PowerShell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="15ef0-147">__Causa radice preliminare__: i tecnici hanno individuato un problema con il provider sottostante della Rete di distribuzione dei contenuti (CDN) di Azure, che è stata distribuita a PowerShell Gallery il 17/5/2016.</span><span class="sxs-lookup"><span data-stu-id="15ef0-147">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="15ef0-148">__Prevenzione__: i tecnici hanno disabilitato la CDN di Azure in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="15ef0-148">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="15ef0-149">__Passaggi successivi__: ricercare la causa radice sottostante e sviluppare una soluzione per evitare che il problema si ripresenti in futuro.</span><span class="sxs-lookup"><span data-stu-id="15ef0-149">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

