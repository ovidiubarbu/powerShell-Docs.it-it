---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Gestione delle chiavi API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002514"
---
# <a name="managing-api-keys"></a><span data-ttu-id="a5cad-103">Gestione delle chiavi API</span><span class="sxs-lookup"><span data-stu-id="a5cad-103">Managing API keys</span></span>

<span data-ttu-id="a5cad-104">PowerShell Gallery supporta la creazione di più chiavi API per supportare una gamma di requisiti per la pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="a5cad-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="a5cad-105">Una chiave API può essere valida per uno o più pacchetti, concede privilegi specifici e ha una data di scadenza.</span><span class="sxs-lookup"><span data-stu-id="a5cad-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5cad-106">Gli utenti che hanno pubblicato in PowerShell Gallery prima dell'introduzione delle chiavi API con ambito avranno una "chiave API con accesso completo".</span><span class="sxs-lookup"><span data-stu-id="a5cad-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="a5cad-107">Le chiavi con accesso completo non presentano i miglioramenti apportati alla sicurezza nelle chiavi API con ambito.</span><span class="sxs-lookup"><span data-stu-id="a5cad-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="a5cad-108">Le chiavi con accesso completo non scadono mai e si applicano a tutti gli elementi appartenenti all'utente.</span><span class="sxs-lookup"><span data-stu-id="a5cad-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="a5cad-109">Se si elimina una chiave di questo tipo, non può essere ricreata.</span><span class="sxs-lookup"><span data-stu-id="a5cad-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="a5cad-110">L'immagine seguente illustra le opzioni disponibili quando si crea una chiave API con ambito.</span><span class="sxs-lookup"><span data-stu-id="a5cad-110">The following image shows the options available when creating a scoped API key.</span></span>

![Creazione di chiavi API](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="a5cad-112">In questo esempio viene creata una chiave API denominata **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="a5cad-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="a5cad-113">Il valore di questa chiave può essere usato per eseguire il push dei pacchetti i cui nomi iniziano con "AzureRM.DataFactory" ed è valido per 365 giorni.</span><span class="sxs-lookup"><span data-stu-id="a5cad-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="a5cad-114">Questo è uno scenario tipico quando diversi team all'interno della stessa organizzazione lavorano su pacchetti diversi.</span><span class="sxs-lookup"><span data-stu-id="a5cad-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="a5cad-115">I membri del team hanno una chiave che concede loro privilegi per il pacchetto specifico su cui lavorano.</span><span class="sxs-lookup"><span data-stu-id="a5cad-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="a5cad-116">Il valore di scadenza impedisce l'uso di chiavi non aggiornate o dimenticate.</span><span class="sxs-lookup"><span data-stu-id="a5cad-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="a5cad-117">Uso dei criteri GLOB</span><span class="sxs-lookup"><span data-stu-id="a5cad-117">Using glob patterns</span></span>

<span data-ttu-id="a5cad-118">Se si lavora su più pacchetti, è possibile usare i criteri di GLOB per abbinare più pacchetti come gruppo.</span><span class="sxs-lookup"><span data-stu-id="a5cad-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="a5cad-119">Le autorizzazioni della chiave API si applicano a tutti i nuovi pacchetti che corrispondono al criterio GLOB.</span><span class="sxs-lookup"><span data-stu-id="a5cad-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="a5cad-120">L'esempio precedente usa il valore di **criterio GLOB** "AzureRM.DataFactory\*".</span><span class="sxs-lookup"><span data-stu-id="a5cad-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="a5cad-121">È possibile eseguire il push di un pacchetto denominato "AzureRm.DataFactoryV2.Netcore" usando questa chiave, poiché il pacchetto corrisponde al criterio GLOB.</span><span class="sxs-lookup"><span data-stu-id="a5cad-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="a5cad-122">Creare chiavi API in modo sicuro</span><span class="sxs-lookup"><span data-stu-id="a5cad-122">Create API keys securely</span></span>

<span data-ttu-id="a5cad-123">Per sicurezza, un valore di chiave appena creato non viene mai visualizzato sullo schermo ed è disponibile solo con il pulsante Copia, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="a5cad-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Creazione di un nuovo valore della chiave API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="a5cad-125">È possibile copiare il valore della chiave API solo immediatamente dopo averlo creato o aggiornato.</span><span class="sxs-lookup"><span data-stu-id="a5cad-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="a5cad-126">Non verrà visualizzato e non sarà possibile accedervi nuovamente dopo che la pagina è stata aggiornata.</span><span class="sxs-lookup"><span data-stu-id="a5cad-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="a5cad-127">Se si perde il valore della chiave, è necessario rigenerare la chiave e copiarla dopo che è stata rigenerata.</span><span class="sxs-lookup"><span data-stu-id="a5cad-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="a5cad-128">Autorizzazioni e scadenza delle chiavi</span><span class="sxs-lookup"><span data-stu-id="a5cad-128">Key permissions and expiration</span></span>

<span data-ttu-id="a5cad-129">Le chiavi API con ambito possono assegnare le autorizzazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a5cad-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="a5cad-130">Push dei nuovi pacchetti</span><span class="sxs-lookup"><span data-stu-id="a5cad-130">Push new packages</span></span>
- <span data-ttu-id="a5cad-131">Push dei pacchetti nuovi o di aggiornamento</span><span class="sxs-lookup"><span data-stu-id="a5cad-131">Push new or update packages</span></span>
- <span data-ttu-id="a5cad-132">Eliminazione di pacchetti dall'elenco</span><span class="sxs-lookup"><span data-stu-id="a5cad-132">Unlist packages</span></span>

<span data-ttu-id="a5cad-133">Ogni nuova chiave ha una scadenza.</span><span class="sxs-lookup"><span data-stu-id="a5cad-133">Every new key has an expiration.</span></span> <span data-ttu-id="a5cad-134">Il valore di scadenza viene misurato in giorni.</span><span class="sxs-lookup"><span data-stu-id="a5cad-134">The expiration value is measured in days.</span></span> <span data-ttu-id="a5cad-135">I valori possibili per la scadenza sono:</span><span class="sxs-lookup"><span data-stu-id="a5cad-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="a5cad-136">1 giorno</span><span class="sxs-lookup"><span data-stu-id="a5cad-136">1 day</span></span>
- <span data-ttu-id="a5cad-137">90 giorni</span><span class="sxs-lookup"><span data-stu-id="a5cad-137">90 days</span></span>
- <span data-ttu-id="a5cad-138">180 giorni</span><span class="sxs-lookup"><span data-stu-id="a5cad-138">180 days</span></span>
- <span data-ttu-id="a5cad-139">270 giorni</span><span class="sxs-lookup"><span data-stu-id="a5cad-139">270 days</span></span>
- <span data-ttu-id="a5cad-140">365 giorni (impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="a5cad-140">365 days (default)</span></span>

<span data-ttu-id="a5cad-141">Queste impostazioni non possono essere modificate dopo la creazione della chiave.</span><span class="sxs-lookup"><span data-stu-id="a5cad-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="a5cad-142">Non è possibile creare una nuova chiave che non scade mai.</span><span class="sxs-lookup"><span data-stu-id="a5cad-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="a5cad-143">Modifica ed eliminazione di chiavi API esistenti</span><span class="sxs-lookup"><span data-stu-id="a5cad-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="a5cad-144">È possibile modificare alcune impostazioni di una chiave esistente.</span><span class="sxs-lookup"><span data-stu-id="a5cad-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="a5cad-145">Come indicato in precedenza, non è possibile modificare l'ambito di protezione per una chiave API esistente o modificare la scadenza.</span><span class="sxs-lookup"><span data-stu-id="a5cad-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="a5cad-146">Le opzioni modificabili sono visualizzate nella schermata seguente:</span><span class="sxs-lookup"><span data-stu-id="a5cad-146">The changeable options are shown in the following screenshot:</span></span>

![Creazione di un nuovo valore della chiave API](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="a5cad-148">Per modificare i pacchetti controllati da una chiave, è possibile scegliere singoli pacchetti dall'elenco o modificare il criterio GLOB.</span><span class="sxs-lookup"><span data-stu-id="a5cad-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="a5cad-149">Facendo clic su **Rigenera** si crea un nuovo valore di chiave.</span><span class="sxs-lookup"><span data-stu-id="a5cad-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="a5cad-150">Proprio come per la creazione iniziale della chiave, è necessario **copiare** il valore della chiave immediatamente dopo averla aggiornata.</span><span class="sxs-lookup"><span data-stu-id="a5cad-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="a5cad-151">L'opzione **Copia** non è disponibile dopo che si è usciti da questa pagina.</span><span class="sxs-lookup"><span data-stu-id="a5cad-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="a5cad-152">Se si fa clic su **Elimina** viene visualizzato un messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="a5cad-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="a5cad-153">Dopo essere stata eliminata, la chiave è inutilizzabile.</span><span class="sxs-lookup"><span data-stu-id="a5cad-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="a5cad-154">Scadenza della chiave</span><span class="sxs-lookup"><span data-stu-id="a5cad-154">Key expiration</span></span>

<span data-ttu-id="a5cad-155">Dieci giorni prima della scadenza, PowerShell Gallery invia un avviso via posta elettronica al titolare dell'account della chiave API.</span><span class="sxs-lookup"><span data-stu-id="a5cad-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="a5cad-156">Dopo la scadenza, la chiave è inutilizzabile.</span><span class="sxs-lookup"><span data-stu-id="a5cad-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="a5cad-157">Nella parte superiore della pagina di gestione delle chiavi API viene visualizzato un messaggio di avviso che indica quali chiavi non sono più valide.</span><span class="sxs-lookup"><span data-stu-id="a5cad-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="a5cad-158">È possibile generare un nuovo valore di chiave.</span><span class="sxs-lookup"><span data-stu-id="a5cad-158">You can generate a new key value.</span></span>
