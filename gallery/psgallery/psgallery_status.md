---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="65741-103">Stato di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="65741-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="65741-104">10/10/2017 - PowerShell Gallery non disponibile per 2 ore 10/10/17</span><span class="sxs-lookup"><span data-stu-id="65741-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="65741-105">__Riepilogo dell'impatto__: per PowerShell Gallery si è verificato un periodo di latenza molto elevata, con conseguenti problemi di connessione intermittente, a partire circa dalle 17.00 (ora del Pacifico) del 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="65741-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="65741-106">Durante la risoluzione del problema, il sito è stato portato offline per 2 ore a partire circa dalle 22.00 (ora del Pacifico).</span><span class="sxs-lookup"><span data-stu-id="65741-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="65741-107">Il sito è stato ripristinato in tempi brevi prima di mezzanotte del 10/10/2017.</span><span class="sxs-lookup"><span data-stu-id="65741-107">The site was restored shortly before midnight 10/10/2017.</span></span>

<span data-ttu-id="65741-108">__Causa principale__: sono ancora in corso le indagini per stabilire la causa dell'elevata latenza.</span><span class="sxs-lookup"><span data-stu-id="65741-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="65741-109">__Risoluzione__: è stato necessario portare offline e ripristinare i servizi Web per risolvere il problema principale.</span><span class="sxs-lookup"><span data-stu-id="65741-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span>

<span data-ttu-id="65741-110">__Passaggi successivi__: continuazione delle indagini per individuare la causa principale del problema originale.</span><span class="sxs-lookup"><span data-stu-id="65741-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="65741-111">01/06/2017 - Distribuzione in Automazione di Azure attualmente non disponibile</span><span class="sxs-lookup"><span data-stu-id="65741-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="65741-112">__Riepilogo dell'impatto__: la distribuzione di elementi con dipendenze in Automazione di Azure da PowerShell Gallery non è attualmente disponibile.</span><span class="sxs-lookup"><span data-stu-id="65741-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="65741-113">L'importazione di elementi da PowerShell Gallery dall'interno di Automazione di Azure è ancora disponibile.</span><span class="sxs-lookup"><span data-stu-id="65741-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>

<span data-ttu-id="65741-114">__Causa radice__: gli elementi con dipendenze che sono stati distribuiti in precedenza in Automazione di Azure non verranno distribuiti in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="65741-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="65741-115">I tecnici hanno identificato un problema nella modalità in cui i modelli ARM vengono generati per gli elementi con dipendenze per la funzionalità di distribuzione in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="65741-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="65741-116">__Risoluzione__: i tecnici stanno lavorando per risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="65741-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="65741-117">La soluzione corrente per gli utenti consiste nell'importare l'elemento da PowerShell Gallery dall'interno di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="65741-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span>

<span data-ttu-id="65741-118">__Passaggi successivi__: i tecnici risolveranno il problema a breve.</span><span class="sxs-lookup"><span data-stu-id="65741-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="65741-119">Nel frattempo, usare la soluzione consigliata.</span><span class="sxs-lookup"><span data-stu-id="65741-119">In the meantime, please use the recommended workaround.</span></span>


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="65741-120">11/04/2017 - Gli utenti non possono accedere con account Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="65741-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="65741-121">__Riepilogo del problema__: alcuni utenti non sono in grado di accedere a PowerShell Gallery usando gli account Azure AD.</span><span class="sxs-lookup"><span data-stu-id="65741-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span>

<span data-ttu-id="65741-122">__Causa radice__: durante un aggiornamento per un'iterazione più sicura con AAD, non è stata eseguita una modifica delle impostazioni.</span><span class="sxs-lookup"><span data-stu-id="65741-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span>
<span data-ttu-id="65741-123">Poiché i test eseguiti per convalidare la modifica non includevano determinati tipi di account AAD, la distribuzione è stata eseguita.</span><span class="sxs-lookup"><span data-stu-id="65741-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="65741-124">__Risoluzione__: I tecnici hanno identificato l'impostazione mancante e corretto il problema.</span><span class="sxs-lookup"><span data-stu-id="65741-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span>

<span data-ttu-id="65741-125">__Passaggi successivi__: verranno modificati i test per includere un set più ampio di tipi di account AAD.</span><span class="sxs-lookup"><span data-stu-id="65741-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="65741-126">27/03/2017 - RISOLTO: impossibile visualizzare singole pagine di moduli e script</span><span class="sxs-lookup"><span data-stu-id="65741-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="65741-127">__Riepilogo del problema__: i collegamenti diretti alle singole pagine di moduli e script in https://www.powershellgallery.com erano interrotti.</span><span class="sxs-lookup"><span data-stu-id="65741-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="65741-128">Il problema era segnalato in tutte le aree.</span><span class="sxs-lookup"><span data-stu-id="65741-128">This was being reported across all the regions.</span></span> <span data-ttu-id="65741-129">Il problema non influiva sui cmdlet di PowerShellGet, ovvero Install-Module, Install-Script, Update-Module, Update-Script e Publish-Module. Publish-Script continuava a funzionare.</span><span class="sxs-lookup"><span data-stu-id="65741-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="65741-130">__Causa radice__: i tecnici hanno identificato la causa in un problema di visualizzazione dei pulsanti per i social media come Facebook nella pagina.</span><span class="sxs-lookup"><span data-stu-id="65741-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="65741-131">__Risoluzione__: tecnici hanno risolto il problema disabilitando le informazioni sul conteggio di Facebook.</span><span class="sxs-lookup"><span data-stu-id="65741-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="65741-132">__Passaggi successivi__: è stato aperto un problema di rilevamento interno per correggere l'uso dell'API di Facebook.</span><span class="sxs-lookup"><span data-stu-id="65741-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="65741-133">15/12/2016 - Impossibile inviare messaggi di posta elettronica tramite il sito Web PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="65741-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="65741-134">__Riepilogo del problema__: tra il 13/12/2016 e il 15/12/2016, tutti i messaggi inviati tramite Contact Owners, Manage Owners, Contact Support o Report Abuse non sono stati ricevuti dagli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="65741-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="65741-135">__Causa radice__: i tecnici hanno identificato la causa in un problema di autenticazione con il server SMTP.</span><span class="sxs-lookup"><span data-stu-id="65741-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="65741-136">__Risoluzione__: i tecnici sono stati in grado di risolvere il problema di autenticazione e ripristinare la connessione al server SMTP.</span><span class="sxs-lookup"><span data-stu-id="65741-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="65741-137">__Passaggi successivi__: se il messaggio di posta elettronica è stato inviato a cgadmin@microsoft.com tramite i collegamenti Contact Owners, Manage Owners, Contact Support o Report Abuse durante questo periodo e non è stata ricevuta alcuna risposta, si prega di rinviare il messaggio.</span><span class="sxs-lookup"><span data-stu-id="65741-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="65741-138">Il team si scusa per l'inconveniente.</span><span class="sxs-lookup"><span data-stu-id="65741-138">We apologize for the inconvenience.</span></span>



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="65741-139">10/08/2016 - risolto: Impossibile inviare messaggi di posta elettronica a cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="65741-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="65741-140">__Riepilogo del problema__: tra il 05/08/2016 e il 10/08/2016 i clienti non hanno potuto inviare messaggi di posta elettronica a cgadmin@microsoft.com o usare la funzionalità Contattaci.</span><span class="sxs-lookup"><span data-stu-id="65741-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="65741-141">__Causa radice__: i tecnici hanno individuato la causa in una modifica della configurazione dell'account di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="65741-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="65741-142">__Risoluzione__: i tecnici hanno lavorato per risolvere il problema di configurazione.</span><span class="sxs-lookup"><span data-stu-id="65741-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="65741-143">__Passaggi successivi__: se in questo periodo è stato usato il collegamento Contattaci o si è inviato un messaggio a cgadmin@microsoft.com senza ricevere risposta, riprovare.</span><span class="sxs-lookup"><span data-stu-id="65741-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="65741-144">Grazie per la pazienza dimostrata.</span><span class="sxs-lookup"><span data-stu-id="65741-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="65741-145">13/07/2016 - download di elementi non riuscito</span><span class="sxs-lookup"><span data-stu-id="65741-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="65741-146">__Riepilogo dell'impatto__: tra l'11/07/2016 e il 13/07/2016, alcuni clienti hanno incontrato problemi di download degli elementi da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="65741-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="65741-147">Il problema si è probabilmente manifestato nei seguenti messaggi di errore restituiti da Install-Module/Install-Script e Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="65741-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="65741-148">__Causa radice preliminare__: i tecnici hanno individuato un problema con la Rete di distribuzione dei contenuti (CDN) di Azure, che è stata distribuita a PowerShell Gallery l'11/07/2016.</span><span class="sxs-lookup"><span data-stu-id="65741-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>
<span data-ttu-id="65741-149">__Prevenzione__: i tecnici hanno disabilitato la CDN di Azure in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="65741-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="65741-150">__Passaggi successivi__: ricercare la causa principale sottostante e sviluppare una soluzione per evitare che questo problema si ripresenti in futuro.</span><span class="sxs-lookup"><span data-stu-id="65741-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="65741-151">19/05/2016 - download di elementi non riuscito</span><span class="sxs-lookup"><span data-stu-id="65741-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="65741-152">__Riepilogo dell'impatto__: tra il 17/05/2016 e il 19/05/2016, alcuni clienti hanno incontrato problemi di download degli elementi da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="65741-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="65741-153">Il problema si è probabilmente manifestato nei seguenti messaggi di errore restituiti da Install-Module/Install-Script e Save-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="65741-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
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

<span data-ttu-id="65741-154">__Causa radice preliminare__: i tecnici hanno individuato un problema con il provider sottostante della Rete di distribuzione dei contenuti (CDN) di Azure, che è stata distribuita a PowerShell Gallery il 17/5/2016.</span><span class="sxs-lookup"><span data-stu-id="65741-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>
<span data-ttu-id="65741-155">__Prevenzione__: i tecnici hanno disabilitato la CDN di Azure in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="65741-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="65741-156">__Passaggi successivi__: ricercare la causa radice sottostante e sviluppare una soluzione per evitare che il problema si ripresenti in futuro.</span><span class="sxs-lookup"><span data-stu-id="65741-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>