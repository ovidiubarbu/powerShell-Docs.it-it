---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Gestione dei proprietari di pacchetti
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328262"
---
# <a name="managing-package-owners"></a><span data-ttu-id="43265-103">Gestione dei proprietari di pacchetti</span><span class="sxs-lookup"><span data-stu-id="43265-103">Managing package owners</span></span>

<span data-ttu-id="43265-104">La proprietà di un pacchetto in PowerShell Gallery è definita dalla persona che ha pubblicato il pacchetto in questione in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="43265-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="43265-105">A volte questi metadati devono essere gestiti anche dopo la pubblicazione del pacchetto iniziale. Questo significa che i metadati del proprietario devono essere modificabili, mentre il pacchetto stesso non lo è.</span><span class="sxs-lookup"><span data-stu-id="43265-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="43265-106">Tutti i proprietari di pacchetti sono pari.</span><span class="sxs-lookup"><span data-stu-id="43265-106">All package owners are peers.</span></span>
<span data-ttu-id="43265-107">Questo significa che qualsiasi proprietario di pacchetto può pubblicare una nuova versione di un pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="43265-108">Significa anche che qualsiasi proprietario di pacchetto può rimuovere qualsiasi altro proprietario di pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="43265-109">Nessun proprietario ha un'autorità maggiore di altri proprietari.</span><span class="sxs-lookup"><span data-stu-id="43265-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="43265-110">Impostazione del proprietario iniziale di un pacchetto</span><span class="sxs-lookup"><span data-stu-id="43265-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="43265-111">Quando un nuovo pacchetto viene pubblicato in PowerShell Gallery, il proprietario iniziale viene definito dall'utente che ha pubblicato il pacchetto in questione.</span><span class="sxs-lookup"><span data-stu-id="43265-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="43265-112">Questo è determinato dal titolare della chiave API usata nel cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="43265-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="43265-113">Aggiunta di proprietari</span><span class="sxs-lookup"><span data-stu-id="43265-113">Adding Owners</span></span>

<span data-ttu-id="43265-114">Dopo che un pacchetto è stato pubblicato in PowerShell Gallery, la procedura per invitare altri utenti a diventare proprietari di tale pacchetto è semplice.</span><span class="sxs-lookup"><span data-stu-id="43265-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="43265-115">[Accedere](https://powershellgallery.com/users/account/LogOn) a PowerShell Gallery con l'account attualmente proprietario di un pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="43265-116">Passare a una pagina di pacchetto tramite la scheda 'Packages' (Pacchetti), eseguendo una ricerca o facendo clic sul proprio nome utente e quindi su [**Manage My Packages**](https://www.powershellgallery.com/account/Packages) (Gestisci pacchetti personali).</span><span class="sxs-lookup"><span data-stu-id="43265-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="43265-117">Dopo aver eseguito l'accesso come proprietario di un pacchetto, fare clic sul collegamento 'Manage Owners' (Gestisci proprietari) disponibile nel lato sinistro.</span><span class="sxs-lookup"><span data-stu-id="43265-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="43265-118">Immettere il nome utente della persona da aggiungere come proprietario e fare clic su 'Aggiungi'.</span><span class="sxs-lookup"><span data-stu-id="43265-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="43265-119">Al nuovo comproprietario viene inviato un messaggio di posta elettronica, come invito a diventare proprietario di un pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="43265-120">Dopo aver fatto clic sul collegamento, l'utente diventa a tutti gli effetti comproprietario del pacchetto e ne ha il pieno controllo, inclusa la possibilità di rimuovere altri utenti come proprietari.</span><span class="sxs-lookup"><span data-stu-id="43265-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="43265-121">**NOTA**: fino a quando non conferma la proprietà, l'utente *non* verrà elencato come proprietario di un pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="43265-122">Nella pagina **Manage Owners** (Gestisci proprietari), nella sezione relativa ai proprietari correnti, verrà visualizzata un'"approvazione in sospeso".</span><span class="sxs-lookup"><span data-stu-id="43265-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="43265-123">Tale invito può essere rimosso, così come è possibile rimuovere altri proprietari.</span><span class="sxs-lookup"><span data-stu-id="43265-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="43265-124">Questo meccanismo di inviti impedisce che gli utenti aggiungano falsamente altri utenti come proprietari dei loro pacchetti.</span><span class="sxs-lookup"><span data-stu-id="43265-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="43265-125">Si tenga presente che i metadati di tipo "Autori" sono semplice testo in formato libero e che soltanto i metadati di tipo "Proprietari" sono controllati.</span><span class="sxs-lookup"><span data-stu-id="43265-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="43265-126">Rimozione di proprietari</span><span class="sxs-lookup"><span data-stu-id="43265-126">Removing Owners</span></span>

<span data-ttu-id="43265-127">Se un pacchetto ha più proprietari ed è necessario rimuoverne uno, seguire questa semplice procedura:</span><span class="sxs-lookup"><span data-stu-id="43265-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="43265-128">[Accedere](https://powershellgallery.com/users/account/LogOn) a PowerShell Gallery con l'account attualmente proprietario del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="43265-129">Passare a una pagina di pacchetto tramite la scheda Packages (Pacchetti), eseguendo una ricerca o facendo clic sul proprio nome utente e quindi su [**Manage My Packages**](https://www.powershellgallery.com/account/Packages) (Gestisci pacchetti personali).</span><span class="sxs-lookup"><span data-stu-id="43265-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="43265-130">Dopo aver eseguito l'accesso come proprietario di un pacchetto, fare clic sul collegamento 'Manage Owners' (Gestisci proprietari) disponibile nel lato sinistro.</span><span class="sxs-lookup"><span data-stu-id="43265-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="43265-131">Fare clic sul collegamento 'Rimuovi' accanto al proprietario da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="43265-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="43265-132">Trasferimento della proprietà di pacchetti</span><span class="sxs-lookup"><span data-stu-id="43265-132">Transferring Package Ownership</span></span>

<span data-ttu-id="43265-133">A volte Microsoft riceve richieste di supporto relative al trasferimento della proprietà di un pacchetto da un utente all'altro. Questa operazione, tuttavia, può essere quasi sempre eseguita dagli utenti in modo autonomo.</span><span class="sxs-lookup"><span data-stu-id="43265-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="43265-134">Il trasferimento della proprietà da un utente a un altro è semplicemente una combinazione delle due procedure descritte in precedenza.</span><span class="sxs-lookup"><span data-stu-id="43265-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="43265-135">Il proprietario corrente invita il nuovo utente a diventare comproprietario e il nuovo utente accetta l'invito;</span><span class="sxs-lookup"><span data-stu-id="43265-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="43265-136">Il nuovo utente rimuove il vecchio utente dall'elenco dei proprietari.</span><span class="sxs-lookup"><span data-stu-id="43265-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="43265-137">La richiesta di supporto può avere due motivi differenti, ma la procedura rimane la stessa.</span><span class="sxs-lookup"><span data-stu-id="43265-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="43265-138">La proprietà del pacchetto cambia da uno sviluppatore a un altro</span><span class="sxs-lookup"><span data-stu-id="43265-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="43265-139">Il pacchetto è stato pubblicato accidentalmente con un account non corretto</span><span class="sxs-lookup"><span data-stu-id="43265-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="43265-140">Pacchetti orfani</span><span class="sxs-lookup"><span data-stu-id="43265-140">Orphaned Packages</span></span>

<span data-ttu-id="43265-141">Anche se raramente, si è presentato anche lo scenario descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="43265-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="43265-142">I pacchetti sono diventati orfani e non è possibile usare l'unico account del proprietario dei pacchetti per aggiungere nuovi proprietari.</span><span class="sxs-lookup"><span data-stu-id="43265-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="43265-143">Di seguito sono riportati alcuni esempi relativi a questo scenario:</span><span class="sxs-lookup"><span data-stu-id="43265-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="43265-144">L'account del proprietario è associato a un indirizzo di posta elettronica che non esiste più e l'utente ha dimenticato la password</span><span class="sxs-lookup"><span data-stu-id="43265-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="43265-145">L'utente registrato ha lasciato l'azienda che produce il pacchetto e non può essere raggiunto per aggiornarne la proprietà</span><span class="sxs-lookup"><span data-stu-id="43265-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="43265-146">A causa di un bug che ha interessato solo pochi pacchetti, il pacchetto risulta senza proprietario in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="43265-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="43265-147">Gli amministratori di PowerShell Gallery possono accedere al collegamento 'Manage Owners' (Gestisci proprietari) per qualsiasi pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="43265-148">Se l'utente che ha inviato la richiesta è il legittimo proprietario di un pacchetto e non è in grado di raggiungere il proprietario corrente per ottenere le autorizzazioni di proprietà, può usare il collegamento 'Report Abuse' (Segnala abusi) per contattare gli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="43265-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="43265-149">Gli amministratori eseguiranno quindi un processo per verificare la proprietà del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="43265-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="43265-150">Se stabiliscono che l'utente deve essere un proprietario del pacchetto, gli amministratori useranno il collegamento 'Manage Owners' (Gestisci proprietari) e invieranno all'utente un invito a diventare proprietario.</span><span class="sxs-lookup"><span data-stu-id="43265-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="43265-151">Gli amministratori agiranno in questo modo solo dopo aver verificato il diritto dell'utente a essere un proprietario. Questo tipo di processo varia a seconda delle circostanze.</span><span class="sxs-lookup"><span data-stu-id="43265-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="43265-152">Spesso gli amministratori useranno l'URL di progetto del pacchetto per contattare il proprietario del progetto stesso. In alternativa, per contattare il proprietario del progetto potranno essere usati Twitter, la posta elettronica o altri sistemi.</span><span class="sxs-lookup"><span data-stu-id="43265-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
