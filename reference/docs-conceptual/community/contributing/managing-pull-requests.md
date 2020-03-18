---
title: Modalità di gestione delle richieste pull
description: Questo articolo illustra in che modo il team PowerShell-Docs gestisce le richieste pull.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060386"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="df70e-103">Gestione delle richieste pull</span><span class="sxs-lookup"><span data-stu-id="df70e-103">Managing pull requests</span></span>

<span data-ttu-id="df70e-104">Questo articolo descrive come vengono gestite le richieste pull nel repository PowerShell-Docs.</span><span class="sxs-lookup"><span data-stu-id="df70e-104">This article documents how we manage pull requests in the PowerShell-Docs repo.</span></span> <span data-ttu-id="df70e-105">Concepito come strumento di lavoro per i membri del team PowerShell-Docs,</span><span class="sxs-lookup"><span data-stu-id="df70e-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="df70e-106">viene pubblicato qui per garantire la trasparenza dei processi per i collaboratori pubblici.</span><span class="sxs-lookup"><span data-stu-id="df70e-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="df70e-107">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="df70e-107">Best practices</span></span>

- <span data-ttu-id="df70e-108">La persona che invia la richiesta pull non deve eseguire il merge della richiesta senza una revisione paritaria.</span><span class="sxs-lookup"><span data-stu-id="df70e-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="df70e-109">Assegnare la revisione paritaria a un revisore quando si invia la richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="df70e-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="df70e-110">L'assegnazione anticipata consente al revisore di rispondere prima con osservazioni di carattere editoriale.</span><span class="sxs-lookup"><span data-stu-id="df70e-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="df70e-111">Usare i commenti per descrivere la natura della modifica o il tipo di revisione richiesta.</span><span class="sxs-lookup"><span data-stu-id="df70e-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="df70e-112">Assicurarsi di @mention il revisore.</span><span class="sxs-lookup"><span data-stu-id="df70e-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="df70e-113">Se, ad esempio, la modifica è secondaria e non è necessaria una revisione tecnica completa, spiegarlo in un commento.</span><span class="sxs-lookup"><span data-stu-id="df70e-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="df70e-114">Passaggi del processo di richiesta pull</span><span class="sxs-lookup"><span data-stu-id="df70e-114">PR Process steps</span></span>

1. <span data-ttu-id="df70e-115">Autore: Creare la richiesta pull</span><span class="sxs-lookup"><span data-stu-id="df70e-115">Writer: Create PR</span></span>
   - <span data-ttu-id="df70e-116">Collegare eventuali problemi risolti dalla richiesta pull</span><span class="sxs-lookup"><span data-stu-id="df70e-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="df70e-117">Usare la funzionalità [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) di GitHub per chiudere il problema</span><span class="sxs-lookup"><span data-stu-id="df70e-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="df70e-118">Autore: Incaricare un revisore della revisione paritaria</span><span class="sxs-lookup"><span data-stu-id="df70e-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="df70e-119">Revisore: corregge e commenta (se necessario)</span><span class="sxs-lookup"><span data-stu-id="df70e-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="df70e-120">Autore: Incorporare il feedback del revisore</span><span class="sxs-lookup"><span data-stu-id="df70e-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="df70e-121">Both: Esaminare il rendering di anteprima</span><span class="sxs-lookup"><span data-stu-id="df70e-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="df70e-122">Both: Esaminare il report di convalida - correggere avvisi ed errori</span><span class="sxs-lookup"><span data-stu-id="df70e-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="df70e-123">Autore: Aggiungere commento di approvazione (includere informazioni Acrolinx)</span><span class="sxs-lookup"><span data-stu-id="df70e-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="df70e-124">Revisore: Contrassegnare la revisione come "approvata"</span><span class="sxs-lookup"><span data-stu-id="df70e-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="df70e-125">Amministratore del repository: Unire la richiesta pull (vedere i criteri di seguito)</span><span class="sxs-lookup"><span data-stu-id="df70e-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="df70e-126">Elenco di controllo del revisore del contenuto</span><span class="sxs-lookup"><span data-stu-id="df70e-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="df70e-127">Per un elenco più completo, vedere l'[elenco di controllo editoriale](editorial-checklist.md).</span><span class="sxs-lookup"><span data-stu-id="df70e-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="df70e-128">Controllare grammatica, stile, concisione, precisione tecnica</span><span class="sxs-lookup"><span data-stu-id="df70e-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="df70e-129">Verificare che gli esempi siano ancora validi per la versione di destinazione</span><span class="sxs-lookup"><span data-stu-id="df70e-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="df70e-130">Controllare il rendering di anteprima</span><span class="sxs-lookup"><span data-stu-id="df70e-130">Check Preview rendering</span></span>
- <span data-ttu-id="df70e-131">Controllare i metadati - ms.date, rimuovere ms.assetid, verificare i campi obbligatori</span><span class="sxs-lookup"><span data-stu-id="df70e-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="df70e-132">Convalidare la correttezza del markdown</span><span class="sxs-lookup"><span data-stu-id="df70e-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="df70e-133">Vedere la Guida di stile per la formattazione di contenuto specifico</span><span class="sxs-lookup"><span data-stu-id="df70e-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="df70e-134">Riorganizzare gli esempi come segue:</span><span class="sxs-lookup"><span data-stu-id="df70e-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="df70e-135">Frasi introduttive</span><span class="sxs-lookup"><span data-stu-id="df70e-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="df70e-136">Codice e output</span><span class="sxs-lookup"><span data-stu-id="df70e-136">Code and output</span></span>
  - <span data-ttu-id="df70e-137">Spiegazione dettagliata del codice (se necessario)</span><span class="sxs-lookup"><span data-stu-id="df70e-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="df70e-138">Verificare l'accuratezza dei collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="df70e-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="df70e-139">Sostituire o rimuovere i collegamenti TechNet/MSDN</span><span class="sxs-lookup"><span data-stu-id="df70e-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="df70e-140">Verificare il numero minimo di reindirizzamenti alla destinazione</span><span class="sxs-lookup"><span data-stu-id="df70e-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="df70e-141">Verificare HTTPS</span><span class="sxs-lookup"><span data-stu-id="df70e-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="df70e-142">Tipo di collegamento corretto</span><span class="sxs-lookup"><span data-stu-id="df70e-142">Correct link type</span></span>
    - <span data-ttu-id="df70e-143">Collegamenti file per i file locali</span><span class="sxs-lookup"><span data-stu-id="df70e-143">File links for local files</span></span>
    - <span data-ttu-id="df70e-144">Collegamenti URL per i file all'esterno del set di documenti</span><span class="sxs-lookup"><span data-stu-id="df70e-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="df70e-145">Rimuovere le impostazioni locali dagli URL</span><span class="sxs-lookup"><span data-stu-id="df70e-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="df70e-146">Semplificare gli URL che puntano a `docs.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="df70e-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="df70e-147">Processo di merge del ramo</span><span class="sxs-lookup"><span data-stu-id="df70e-147">Branch Merge Process</span></span>

<span data-ttu-id="df70e-148">Il ramo di staging è l'unico ramo che deve essere unito in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="df70e-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="df70e-149">I merge da rami di breve durata (in uso) devono essere sottoposti a squash.</span><span class="sxs-lookup"><span data-stu-id="df70e-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="df70e-150">*Merge da/a*</span><span class="sxs-lookup"><span data-stu-id="df70e-150">*Merge from/to*</span></span>  | <span data-ttu-id="df70e-151">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="df70e-151">*release-branch*</span></span> | <span data-ttu-id="df70e-152">*staging*</span><span class="sxs-lookup"><span data-stu-id="df70e-152">*staging*</span></span>        | <span data-ttu-id="df70e-153">*live*</span><span class="sxs-lookup"><span data-stu-id="df70e-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="df70e-154">*working-branch*</span><span class="sxs-lookup"><span data-stu-id="df70e-154">*working-branch*</span></span> | <span data-ttu-id="df70e-155">squash e merge</span><span class="sxs-lookup"><span data-stu-id="df70e-155">squash and merge</span></span> | <span data-ttu-id="df70e-156">squash e merge</span><span class="sxs-lookup"><span data-stu-id="df70e-156">squash and merge</span></span> | <span data-ttu-id="df70e-157">Non consentito</span><span class="sxs-lookup"><span data-stu-id="df70e-157">Not allowed</span></span> |
| <span data-ttu-id="df70e-158">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="df70e-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="df70e-159">merge</span><span class="sxs-lookup"><span data-stu-id="df70e-159">merge</span></span>            | <span data-ttu-id="df70e-160">Non consentito</span><span class="sxs-lookup"><span data-stu-id="df70e-160">Not allowed</span></span> |
| <span data-ttu-id="df70e-161">*staging*</span><span class="sxs-lookup"><span data-stu-id="df70e-161">*staging*</span></span>        | <span data-ttu-id="df70e-162">riassegna</span><span class="sxs-lookup"><span data-stu-id="df70e-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="df70e-163">merge</span><span class="sxs-lookup"><span data-stu-id="df70e-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="df70e-164">Elenco di controllo della fusione di richieste pull</span><span class="sxs-lookup"><span data-stu-id="df70e-164">PR Merger checklist</span></span>

- <span data-ttu-id="df70e-165">Revisione del contenuto completata</span><span class="sxs-lookup"><span data-stu-id="df70e-165">Content review complete</span></span>
- <span data-ttu-id="df70e-166">Ramo di destinazione corretto per la modifica</span><span class="sxs-lookup"><span data-stu-id="df70e-166">Correct target branch for the change</span></span>
- <span data-ttu-id="df70e-167">Nessun conflitto di merge</span><span class="sxs-lookup"><span data-stu-id="df70e-167">No merge conflicts</span></span>
- <span data-ttu-id="df70e-168">Tutti i passaggi di convalida e compilazione superati</span><span class="sxs-lookup"><span data-stu-id="df70e-168">All validation and build step pass</span></span>
  - <span data-ttu-id="df70e-169">Avvisi e suggerimenti devono essere corretti (vedere le [note](#notes) per le eccezioni)</span><span class="sxs-lookup"><span data-stu-id="df70e-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="df70e-170">Nessun collegamento interrotto</span><span class="sxs-lookup"><span data-stu-id="df70e-170">No broken links</span></span>
- <span data-ttu-id="df70e-171">Merge in base alla tabella</span><span class="sxs-lookup"><span data-stu-id="df70e-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="df70e-172">Note</span><span class="sxs-lookup"><span data-stu-id="df70e-172">Notes</span></span>

<span data-ttu-id="df70e-173">È possibile ignorare gli avvisi seguenti:</span><span class="sxs-lookup"><span data-stu-id="df70e-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="df70e-174">Quando si unisce una richiesta pull, l'elemento HEAD del ramo di destinazione viene modificato.</span><span class="sxs-lookup"><span data-stu-id="df70e-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="df70e-175">Eventuali richieste pull aperte basate sull'elemento HEAD precedente sono ora obsolete.</span><span class="sxs-lookup"><span data-stu-id="df70e-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="df70e-176">La richiesta pull obsoleta può essere unita usando i diritti di amministratore per eseguire l'override degli avvisi di merge in GitHub.</span><span class="sxs-lookup"><span data-stu-id="df70e-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="df70e-177">Questa operazione può essere eseguita in modo sicuro se le richieste pull unite in precedenza non hanno toccato gli stessi file.</span><span class="sxs-lookup"><span data-stu-id="df70e-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="df70e-178">Tuttavia, fare clic sul pulsante di **aggiornamento del ramo** è l'opzione più sicura.</span><span class="sxs-lookup"><span data-stu-id="df70e-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="df70e-179">È possibile che siano presenti conflitti non risolti che devono essere corretti.</span><span class="sxs-lookup"><span data-stu-id="df70e-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="df70e-180">Pubblicazione in Live</span><span class="sxs-lookup"><span data-stu-id="df70e-180">Publishing to Live</span></span>

<span data-ttu-id="df70e-181">Periodicamente, le modifiche accumulate nel ramo `staging` devono essere pubblicate nel sito Web reale.</span><span class="sxs-lookup"><span data-stu-id="df70e-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="df70e-182">Questa operazione richiede il merge del ramo `staging` nel ramo `live`.</span><span class="sxs-lookup"><span data-stu-id="df70e-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="df70e-183">Il ramo `staging` deve essere unito a `live` almeno una volta alla settimana.</span><span class="sxs-lookup"><span data-stu-id="df70e-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="df70e-184">Il ramo `staging` deve essere unito a `live` dopo qualsiasi modifica significativa.</span><span class="sxs-lookup"><span data-stu-id="df70e-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="df70e-185">Modifiche a 50 o più file</span><span class="sxs-lookup"><span data-stu-id="df70e-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="df70e-186">Dopo il merge di un ramo di rilascio</span><span class="sxs-lookup"><span data-stu-id="df70e-186">After merging a release branch</span></span>
  - <span data-ttu-id="df70e-187">Modifiche alle configurazioni di repositori o set di documenti (docfx.json, configurazioni OPS, script di compilazione e così via)</span><span class="sxs-lookup"><span data-stu-id="df70e-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="df70e-188">Modifiche al file di reindirizzamento</span><span class="sxs-lookup"><span data-stu-id="df70e-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="df70e-189">Modifiche al sommario</span><span class="sxs-lookup"><span data-stu-id="df70e-189">Changes to the TOC</span></span>
  - <span data-ttu-id="df70e-190">Dopo il merge di un ramo di "progetto" (riorganizzazione contenuto, aggiornamento in blocco e così via)</span><span class="sxs-lookup"><span data-stu-id="df70e-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
