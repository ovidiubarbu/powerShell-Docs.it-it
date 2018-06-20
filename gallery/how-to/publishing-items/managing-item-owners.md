---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Gestione dei proprietari di elementi
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222108"
---
# <a name="managing-item-owners"></a><span data-ttu-id="80886-103">Gestione dei proprietari di elementi</span><span class="sxs-lookup"><span data-stu-id="80886-103">Managing item owners</span></span>

<span data-ttu-id="80886-104">La proprietà di un elemento in PowerShell Gallery è definita dalla persona che ha pubblicato l'elemento in questione in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80886-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="80886-105">A volte questi metadati devono essere gestiti anche dopo la pubblicazione dell'elemento iniziale. Questo significa che i metadati del proprietario devono essere modificabili, mentre l'elemento stesso non lo è.</span><span class="sxs-lookup"><span data-stu-id="80886-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="80886-106">Tutti i proprietari di elementi hanno pari diritti.</span><span class="sxs-lookup"><span data-stu-id="80886-106">All item owners are peers.</span></span>
<span data-ttu-id="80886-107">Questo significa che qualsiasi proprietario di elemento può pubblicare una nuova versione dell'elemento stesso.</span><span class="sxs-lookup"><span data-stu-id="80886-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="80886-108">Significa anche che qualsiasi proprietario di elemento può rimuovere un altro proprietario di elemento.</span><span class="sxs-lookup"><span data-stu-id="80886-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="80886-109">Nessun proprietario ha un'autorità maggiore di altri proprietari.</span><span class="sxs-lookup"><span data-stu-id="80886-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="80886-110">Impostazione del proprietario iniziale di un elemento</span><span class="sxs-lookup"><span data-stu-id="80886-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="80886-111">Quando un elemento viene pubblicato in PowerShell Gallery, il proprietario iniziale viene definito dall'utente che ha pubblicato l'elemento in questione.</span><span class="sxs-lookup"><span data-stu-id="80886-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="80886-112">Questo è determinato dal titolare della chiave API usata nel cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="80886-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="80886-113">Aggiunta di proprietari</span><span class="sxs-lookup"><span data-stu-id="80886-113">Adding Owners</span></span>

<span data-ttu-id="80886-114">Dopo che un elemento è stato pubblicato in PowerShell Gallery, la procedura per invitare altri utenti a diventare proprietari di tale elemento è semplice.</span><span class="sxs-lookup"><span data-stu-id="80886-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="80886-115">[Accedere](https://powershellgallery.com/users/account/LogOn) a PowerShell Gallery con l'account attualmente proprietario dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="80886-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="80886-116">Passare a una pagina di tipo elemento usando la scheda 'Elementi', eseguendo una ricerca o facendo clic sul proprio nome utente e quindi su [**Manage My Items**](https://www.powershellgallery.com/account/Packages) (Gestisci elementi personali).</span><span class="sxs-lookup"><span data-stu-id="80886-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="80886-117">Dopo aver eseguito l'accesso come proprietario di un elemento, nel lato sinistro è disponibile il collegamento 'Manage Owners' (Gestisci proprietari) su cui fare clic.</span><span class="sxs-lookup"><span data-stu-id="80886-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="80886-118">Immettere il nome utente della persona da aggiungere come proprietario e fare clic su 'Aggiungi'.</span><span class="sxs-lookup"><span data-stu-id="80886-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="80886-119">Al nuovo comproprietario viene inviato un messaggio di posta elettronica, come invito a diventare proprietario di un elemento.</span><span class="sxs-lookup"><span data-stu-id="80886-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="80886-120">Dopo aver fatto clic sul collegamento, l'utente diventa a tutti gli effetti comproprietario dell'elemento e ne ha il pieno controllo, inclusa la possibilità di rimuovere altri utenti come proprietari.</span><span class="sxs-lookup"><span data-stu-id="80886-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="80886-121">**NOTA**: fino a quando non conferma la proprietà, l'utente *non* verrà elencato come proprietario di un elemento.</span><span class="sxs-lookup"><span data-stu-id="80886-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="80886-122">Nella pagina **Manage Owners** (Gestisci proprietari), nella sezione relativa ai proprietari correnti, verrà visualizzata un'"approvazione in sospeso".</span><span class="sxs-lookup"><span data-stu-id="80886-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="80886-123">Tale invito può essere rimosso, così come è possibile rimuovere altri proprietari.</span><span class="sxs-lookup"><span data-stu-id="80886-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="80886-124">Questo meccanismo di inviti impedisce che gli utenti aggiungano falsamente altri utenti come proprietari dei loro elementi.</span><span class="sxs-lookup"><span data-stu-id="80886-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="80886-125">Si tenga presente che i metadati di tipo "Autori" sono semplice testo in formato libero e che soltanto i metadati di tipo "Proprietari" sono controllati.</span><span class="sxs-lookup"><span data-stu-id="80886-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="80886-126">Rimozione di proprietari</span><span class="sxs-lookup"><span data-stu-id="80886-126">Removing Owners</span></span>

<span data-ttu-id="80886-127">Se un elemento ha più proprietari ed è necessario rimuoverne uno, seguire questa semplice procedura:</span><span class="sxs-lookup"><span data-stu-id="80886-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="80886-128">[Accedere](https://powershellgallery.com/users/account/LogOn) a PowerShell Gallery con l'account attualmente proprietario dell'elemento;</span><span class="sxs-lookup"><span data-stu-id="80886-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="80886-129">Passare a una pagina di tipo elemento usando la scheda Elementi, eseguendo una ricerca o facendo clic sul proprio nome utente e quindi su [**Manage My Items**](https://www.powershellgallery.com/account/Packages) (Gestisci elementi personali).</span><span class="sxs-lookup"><span data-stu-id="80886-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="80886-130">Dopo aver eseguito l'accesso come proprietario di un elemento, nel lato sinistro è disponibile il collegamento 'Manage Owners' (Gestisci proprietari) su cui fare clic;</span><span class="sxs-lookup"><span data-stu-id="80886-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="80886-131">Fare clic sul collegamento 'Rimuovi' accanto al proprietario da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="80886-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="80886-132">Trasferimento della proprietà degli elementi</span><span class="sxs-lookup"><span data-stu-id="80886-132">Transferring Item Ownership</span></span>

<span data-ttu-id="80886-133">A volte Microsoft riceve richieste di supporto relative al trasferimento della proprietà di un elemento da un utente all'altro. Questa operazione, tuttavia, può essere quasi sempre eseguita dagli utenti in modo autonomo.</span><span class="sxs-lookup"><span data-stu-id="80886-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="80886-134">Il trasferimento della proprietà da un utente a un altro è semplicemente una combinazione delle due procedure descritte in precedenza.</span><span class="sxs-lookup"><span data-stu-id="80886-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="80886-135">Il proprietario corrente invita il nuovo utente a diventare comproprietario e il nuovo utente accetta l'invito;</span><span class="sxs-lookup"><span data-stu-id="80886-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="80886-136">Il nuovo utente rimuove il vecchio utente dall'elenco dei proprietari.</span><span class="sxs-lookup"><span data-stu-id="80886-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="80886-137">La richiesta di supporto può avere due motivi differenti, ma la procedura rimane la stessa.</span><span class="sxs-lookup"><span data-stu-id="80886-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="80886-138">La proprietà dell'elemento cambia da uno sviluppatore a un altro</span><span class="sxs-lookup"><span data-stu-id="80886-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="80886-139">L'elemento è stato pubblicato accidentalmente con un account non corretto</span><span class="sxs-lookup"><span data-stu-id="80886-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="80886-140">Elenchi orfani</span><span class="sxs-lookup"><span data-stu-id="80886-140">Orphaned Items</span></span>

<span data-ttu-id="80886-141">Anche se raramente, si è presentato anche lo scenario descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="80886-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="80886-142">Gli elementi sono diventati orfani e non è possibile usare soltanto l'account del proprietario degli elementi per aggiungere nuovi proprietari.</span><span class="sxs-lookup"><span data-stu-id="80886-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="80886-143">Di seguito sono riportati alcuni esempi relativi a questo scenario:</span><span class="sxs-lookup"><span data-stu-id="80886-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="80886-144">L'account del proprietario è associato a un indirizzo di posta elettronica che non esiste più e l'utente ha dimenticato la password</span><span class="sxs-lookup"><span data-stu-id="80886-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="80886-145">L'utente registrato ha lasciato l'azienda che produce l'elemento e non può essere raggiunto per aggiornarne la proprietà</span><span class="sxs-lookup"><span data-stu-id="80886-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="80886-146">A causa di un bug che ha interessato solo pochi elementi, l'elemento risulta senza proprietario in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80886-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="80886-147">Gli amministratori di PowerShell Gallery possono accedere al collegamento 'Manage Owners' (Gestisci proprietari) per qualsiasi elemento.</span><span class="sxs-lookup"><span data-stu-id="80886-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="80886-148">Se l'utente che ha inviato la richiesta è il legittimo proprietario di un elemento e non è in grado di raggiungere il proprietario corrente per ottenere le autorizzazioni di proprietà, può usare il collegamento 'Report Abuse' (Segnala abusi) per contattare gli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80886-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="80886-149">Gli amministratori eseguiranno quindi un processo per verificare la proprietà dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="80886-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="80886-150">Se stabiliscono che l'utente deve essere un proprietario dell'elemento, gli amministratori useranno il collegamento 'Manage Owners' (Gestisci proprietari) e invieranno all'utente un invito a diventare proprietario.</span><span class="sxs-lookup"><span data-stu-id="80886-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="80886-151">Gli amministratori agiranno in questo modo solo dopo aver verificato il diritto dell'utente a essere un proprietario. Questo tipo di processo varia a seconda delle circostanze.</span><span class="sxs-lookup"><span data-stu-id="80886-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="80886-152">Spesso gli amministratori useranno l'URL di progetto dell'elemento per contattare il proprietario del progetto stesso. In alternativa, per contattare il proprietario del progetto potranno essere usati Twitter, la posta elettronica o altri sistemi.</span><span class="sxs-lookup"><span data-stu-id="80886-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>