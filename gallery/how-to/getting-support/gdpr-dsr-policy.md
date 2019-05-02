---
ms.date: 03/27/2018
contributor: JKeithB
keywords: raccolta,powershell,psgallery,GDPR
title: Conformità al regolamento GDPR di PowerShell Gallery
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084233"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="6d01d-103">Conformità al regolamento GDPR di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="6d01d-104">Panoramica</span><span class="sxs-lookup"><span data-stu-id="6d01d-104">Overview</span></span>

<span data-ttu-id="6d01d-105">A maggio 2018 è entrata in vigore una normativa europea sulla privacy, il Regolamento generale sulla protezione dei dati (GDPR, General Data Protection Regulation).</span><span class="sxs-lookup"><span data-stu-id="6d01d-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="6d01d-106">La normativa GDPR impone nuove regole ad aziende, enti governativi, enti no profit e altre organizzazioni che offrono beni e servizi a residenti dell'Unione Europea (UE) o che raccolgono e analizzano dati associati a residenti UE.</span><span class="sxs-lookup"><span data-stu-id="6d01d-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="6d01d-107">La normativa GDPR è valida ovunque ci si trovi.</span><span class="sxs-lookup"><span data-stu-id="6d01d-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="6d01d-108">Questo articolo illustra le procedure per eliminare dati personali da PowerShell Gallery e può essere usato per adempiere gli obblighi previsti dalla normativa.</span><span class="sxs-lookup"><span data-stu-id="6d01d-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="6d01d-109">Per informazioni generali sulla normativa GDPR, vedere la [sezione GDPR del portale Service Trust](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="6d01d-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="6d01d-110">Dati personali identificabili</span><span class="sxs-lookup"><span data-stu-id="6d01d-110">Personally identifiable data</span></span>

<span data-ttu-id="6d01d-111">PowerShell Gallery archivia le informazioni seguenti, che possono essere trasmesse dagli utenti e includere informazioni personali:</span><span class="sxs-lookup"><span data-stu-id="6d01d-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="6d01d-112">Account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="6d01d-113">Pacchetti pubblicati in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="6d01d-114">Corrispondenza di posta elettronica con il team PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="6d01d-115">La maggior parte degli utenti non crea un account di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="6d01d-116">Non è necessario un account, a meno che non si intenda pubblicare un pacchetto o usare la funzionalità "Proprietario contatto" in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="6d01d-117">A parte la corrispondenza di posta elettronica avviata dall'utente, PowerShell Gallery non archivia dati personali identificabili per utenti che non hanno creato un account.</span><span class="sxs-lookup"><span data-stu-id="6d01d-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="6d01d-118">Gli utenti che creano un account PowerShell Gallery possono pubblicare pacchetti in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="6d01d-119">È previsto che tali pacchetti siano costituiti da codice PowerShell, ma possono anche contenere altre informazioni, incluse informazioni personali.</span><span class="sxs-lookup"><span data-stu-id="6d01d-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="6d01d-120">Le informazioni seguenti visualizzano come ottenere tutti i pacchetti pubblicati in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="6d01d-121">Esportazione DSR dei dati di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="6d01d-122">Le sezioni seguenti descrivono come PowerShell Gallery supporta le richieste DSR (Data Subject Rights, Diritti del soggetto dei dati) e illustrano come esportare le informazioni archiviate in PowerShell Gallery e come richiedere l'eliminazione di queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="6d01d-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="6d01d-123">Posta elettronica</span><span class="sxs-lookup"><span data-stu-id="6d01d-123">Email</span></span>

<span data-ttu-id="6d01d-124">La corrispondenza tramite posta elettronica può includere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="6d01d-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="6d01d-125">Messaggio di posta elettronica inviato ai proprietari di pacchetti di PowerShell Gallery se l'analisi del codice rileva un problema con un pacchetto pubblicato da tali proprietari in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="6d01d-126">Messaggio di posta elettronica inviato da qualsiasi utente al team di PowerShell Gallery usando l'indirizzo di posta elettronica disponibile nella pagina "Contattaci" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="6d01d-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="6d01d-127">Utenti registrati che usano la funzionalità "Contact Owner" (Proprietario contatto) in PowerShell Gallery per inviare posta elettronica al proprietario di un pacchetto di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="6d01d-128">Per i messaggi di posta elettronica inviati da o a PowerShell Gallery sono previsti criteri di conservazione di 90 giorni, che supportano eventuali verifiche di sicurezza nel caso in cui venga rilevato codice dannoso in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="6d01d-129">In bse ai criteri i messaggi di posta elettronica vengono eliminati dopo 90 giorni.</span><span class="sxs-lookup"><span data-stu-id="6d01d-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="6d01d-130">È possibile richiedere copie di tutti i messaggi di posta elettronica scambiati tra l'indirizzo di posta elettronica dell'utente e PowerShell Gallery nei 90 giorni precedenti.</span><span class="sxs-lookup"><span data-stu-id="6d01d-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="6d01d-131">Per richiedere questa corrispondenza, inviare un messaggio di posta elettronica a [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), con il titolo: "DSR Request for emails relating to this account" (Richiesta DSR per i messaggi di posta elettronica relativi a questo account).</span><span class="sxs-lookup"><span data-stu-id="6d01d-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="6d01d-132">Nel corpo del messaggio indicare le informazioni richieste, ad esempio: Please send all emails sent to or received from this email address (Inviare tutti i messaggi di posta elettronica inviati o ricevuti da questo indirizzo di posta elettronica). Entro 7 giorni lavorativi si riceveranno tutti i messaggi che includono l'indirizzo di posta elettronica risalenti a un massimo di 90 giorni dalla data della richiesta.</span><span class="sxs-lookup"><span data-stu-id="6d01d-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="6d01d-133">Informazioni sull'account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="6d01d-134">Se è stato creato un account di PowerShell Gallery, è possibile trovare tutte le informazioni personali archiviate in PowerShell Gallery seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="6d01d-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="6d01d-135">Accedere a PowerShell Gallery, quindi fare clic sul proprio nome utente</span><span class="sxs-lookup"><span data-stu-id="6d01d-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="6d01d-136">La pagina successiva visualizzata è la pagina Account, che include l'indirizzo di posta elettronica usato per l'account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="6d01d-137">Se sono stati creati più account in PowerShell Gallery, è necessario ripetere questi passaggi per ogni account.</span><span class="sxs-lookup"><span data-stu-id="6d01d-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="6d01d-138">Pacchetti in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="6d01d-139">Per facilitare l'esportazione di pacchetti pubblicati in PowerShell Gallery, Microsoft ha pubblicato lo script "GetPSGalleryItemsForAuthor" in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="6d01d-140">Questo script esporta una copia di ogni versione di ogni pacchetto incluso in PowerShell Gallery sulla base delle informazioni dell'autore memorizzate nel pacchetto.</span><span class="sxs-lookup"><span data-stu-id="6d01d-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="6d01d-141">L'autore viene archiviato nel manifesto del pacchetto al momento della pubblicazione del pacchetto stesso.</span><span class="sxs-lookup"><span data-stu-id="6d01d-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="6d01d-142">Non vi è garanzia che l'identità dell'autore corrisponda all'account usato in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6d01d-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="6d01d-143">Se si usa un altro valore nel campo Autore, è necessario specificare tale valore quando si usa questo script.</span><span class="sxs-lookup"><span data-stu-id="6d01d-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="6d01d-144">È possibile scaricare lo script usando il comando PowerShell seguente:</span><span class="sxs-lookup"><span data-stu-id="6d01d-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="6d01d-145">Quindi è possibile eseguire direttamente lo script eseguendo il comando PowerShell seguente:</span><span class="sxs-lookup"><span data-stu-id="6d01d-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="6d01d-146">Viene richiesto di specificare l'autore e la cartella del sistema in cui salvare i pacchetti.</span><span class="sxs-lookup"><span data-stu-id="6d01d-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="6d01d-147">Eliminazione dei dati personali da PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6d01d-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="6d01d-148">Per eliminare l'account di PowerShell Gallery o qualsiasi pacchetto di proprietà dell'utente in PowerShell Gallery, inviare un messaggio di posta elettronica all'indirizzo cgadmin@microsoft.com con il titolo: "GDPR Request for items relating to this account" (Richiesta GDPR per elementi associati a questo account).</span><span class="sxs-lookup"><span data-stu-id="6d01d-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="6d01d-149">Nel corpo del messaggio indicare le informazioni da eliminare.</span><span class="sxs-lookup"><span data-stu-id="6d01d-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="6d01d-150">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6d01d-150">For example:</span></span>

- <span data-ttu-id="6d01d-151">Please delete version x.y.z of my package "package name" (Eliminare la versione x.y.z del mio pacchetto "nome pacchetto")</span><span class="sxs-lookup"><span data-stu-id="6d01d-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="6d01d-152">Please delete all versions of my package "package name" (Eliminare tutte le versioni del mio pacchetto "nome pacchetto")</span><span class="sxs-lookup"><span data-stu-id="6d01d-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="6d01d-153">Please delete my PowerShell Gallery account (Eliminare il mio account PowerShell Gallery)</span><span class="sxs-lookup"><span data-stu-id="6d01d-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="6d01d-154">Gli amministratori di PowerShell Gallery risponderanno entro 7 giorni lavorativi.</span><span class="sxs-lookup"><span data-stu-id="6d01d-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="6d01d-155">I pacchetti specificati verranno eliminati entro 30 giorni dall'invio della richiesta.</span><span class="sxs-lookup"><span data-stu-id="6d01d-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
