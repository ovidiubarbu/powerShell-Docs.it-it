---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="76fb4-103">Stato di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="76fb4-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="76fb4-104">27/03/2017 - RISOLTO: impossibile visualizzare singole pagine di moduli e script</span><span class="sxs-lookup"><span data-stu-id="76fb4-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="76fb4-105">__Riepilogo del problema__: i collegamenti diretti alle singole pagine di moduli e script in https://www.powershellgallery.com erano interrotti.</span><span class="sxs-lookup"><span data-stu-id="76fb4-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="76fb4-106">Il problema era segnalato in tutte le aree.</span><span class="sxs-lookup"><span data-stu-id="76fb4-106">This was being reported across all the regions.</span></span> <span data-ttu-id="76fb4-107">Il problema non influiva sui cmdlet di PowerShellGet, in altre parole Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module e Publish-Script continuavano a funzionare.</span><span class="sxs-lookup"><span data-stu-id="76fb4-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="76fb4-108">__Causa radice__: i tecnici hanno identificato la causa in un problema di visualizzazione dei pulsanti per i social media come Facebook nella pagina.</span><span class="sxs-lookup"><span data-stu-id="76fb4-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="76fb4-109">__Risoluzione__: tecnici hanno risolto il problema disabilitando le informazioni sul conteggio di Facebook.</span><span class="sxs-lookup"><span data-stu-id="76fb4-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="76fb4-110">__Passaggi successivi__: è stato aperto un problema di rilevamento interno per correggere l'uso dell'API di Facebook.</span><span class="sxs-lookup"><span data-stu-id="76fb4-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="76fb4-111">15/12/2016 - Impossibile inviare messaggi di posta elettronica tramite il sito Web PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="76fb4-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="76fb4-112">__Riepilogo del problema__: tra il 13/12/2016 e il 15/12/2016, tutti i messaggi inviati tramite Contact Owners, Manage Owners, Contact Support o Report Abuse non sono stati ricevuti dagli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="76fb4-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="76fb4-113">__Causa radice__: i tecnici hanno identificato la causa in un problema di autenticazione con il server SMTP.</span><span class="sxs-lookup"><span data-stu-id="76fb4-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="76fb4-114">__Risoluzione__: i tecnici sono stati in grado di risolvere il problema di autenticazione e ripristinare la connessione al server SMTP.</span><span class="sxs-lookup"><span data-stu-id="76fb4-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="76fb4-115">__Passaggi successivi__: se il messaggio di posta elettronica è stato inviato a cgadmin@microsoft.com tramite i collegamenti Contact Owners, Manage Owners, Contact Support o Report Abuse durante questo periodo e non è stata ricevuta alcuna risposta, si prega di rinviare il messaggio.</span><span class="sxs-lookup"><span data-stu-id="76fb4-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="76fb4-116">Il team si scusa per l'inconveniente.</span><span class="sxs-lookup"><span data-stu-id="76fb4-116">We apologize for the inconvenience.</span></span>


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="76fb4-117">10/08/2016 - risolto: Impossibile inviare messaggi di posta elettronica a cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="76fb4-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="76fb4-118">__Riepilogo del problema__: tra il 05/08/2016 e il 10/08/2016 i clienti non hanno potuto inviare messaggi di posta elettronica a cgadmin@microsoft.com o usare la funzionalità Contattaci.</span><span class="sxs-lookup"><span data-stu-id="76fb4-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="76fb4-119">__Causa radice__: i tecnici hanno individuato la causa in una modifica della configurazione dell'account di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="76fb4-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="76fb4-120">__Risoluzione__: i tecnici hanno lavorato per risolvere il problema di configurazione.</span><span class="sxs-lookup"><span data-stu-id="76fb4-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="76fb4-121">__Passaggi successivi__: se in questo periodo è stato usato il collegamento Contattaci o si è inviato un messaggio a cgadmin@microsoft.com senza ricevere risposta, riprovare.</span><span class="sxs-lookup"><span data-stu-id="76fb4-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="76fb4-122">Grazie per la pazienza dimostrata.</span><span class="sxs-lookup"><span data-stu-id="76fb4-122">Thank you for your patience.</span></span>