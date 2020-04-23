---
title: Come inviare le richieste pull
description: Questo articolo spiega come inviare le richieste pull al repository PowerShell-Docs.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 2600049b06da5ad4869b6ff335f00bc40c2d1c22
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79060236"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="c3992-103">Come inviare le richieste pull</span><span class="sxs-lookup"><span data-stu-id="c3992-103">How to submit pull requests</span></span>

<span data-ttu-id="c3992-104">Per apportare modifiche al contenuto, inviare una richiesta pull dal fork.</span><span class="sxs-lookup"><span data-stu-id="c3992-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="c3992-105">Prima di eseguire il merge di una richiesta pull, è necessaria una revisione.</span><span class="sxs-lookup"><span data-stu-id="c3992-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="c3992-106">Per ottenere risultati ottimali, esaminare l'[elenco di controllo editoriale](editorial-checklist.md) prima di inviare la richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="c3992-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="c3992-107">Specificare come destinazione il ramo corretto</span><span class="sxs-lookup"><span data-stu-id="c3992-107">Target the correct branch</span></span>

<span data-ttu-id="c3992-108">Tutte le richieste pull devono avere come destinazione il ramo `staging`.</span><span class="sxs-lookup"><span data-stu-id="c3992-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="c3992-109">Le modifiche non devono mai essere inviate al ramo `live`.</span><span class="sxs-lookup"><span data-stu-id="c3992-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="c3992-110">Le modifiche apportate nel ramo `staging` vengono unite in `live`, sovrascrivendo le modifiche apportate a `live`.</span><span class="sxs-lookup"><span data-stu-id="c3992-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="c3992-111">Se si sta inviando una modifica che si applica solo a una versione non rilasciata di PowerShell, cercare un ramo di rilascio per tale versione.</span><span class="sxs-lookup"><span data-stu-id="c3992-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="c3992-112">La richiesta pull deve essere destinata al ramo di rilascio.</span><span class="sxs-lookup"><span data-stu-id="c3992-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="c3992-113">I rami di rilascio hanno il seguente modello di denominazione: `release-<version>`.</span><span class="sxs-lookup"><span data-stu-id="c3992-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="c3992-114">Ottimizzare il processo di richiesta pull per tutti</span><span class="sxs-lookup"><span data-stu-id="c3992-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="c3992-115">Più semplice e più mirata è la richiesta pull, più è rapida l'esecuzione della revisione e del merge.</span><span class="sxs-lookup"><span data-stu-id="c3992-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="c3992-116">Evitare i rami che aggiornano un numero elevato di file o contengono modifiche non correlate</span><span class="sxs-lookup"><span data-stu-id="c3992-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="c3992-117">Evitare di creare richieste pull contenenti modifiche non correlate.</span><span class="sxs-lookup"><span data-stu-id="c3992-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="c3992-118">Separare gli aggiornamenti secondari degli articoli esistenti dai nuovi articoli o da riscritture importanti.</span><span class="sxs-lookup"><span data-stu-id="c3992-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="c3992-119">Lavorare a queste modifiche in rami di lavoro separati.</span><span class="sxs-lookup"><span data-stu-id="c3992-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="c3992-120">Le modifiche in blocco creano richieste pull con un numero elevato di file modificati.</span><span class="sxs-lookup"><span data-stu-id="c3992-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="c3992-121">Limitare le richieste pull a un massimo di 50 file modificati.</span><span class="sxs-lookup"><span data-stu-id="c3992-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="c3992-122">Le richieste pull di grandi dimensioni sono difficili da esaminare e più soggette a errori.</span><span class="sxs-lookup"><span data-stu-id="c3992-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="c3992-123">Ridenominazione o eliminazione di file</span><span class="sxs-lookup"><span data-stu-id="c3992-123">Renaming or deleting files</span></span>

<span data-ttu-id="c3992-124">Se si rinominano o eliminano file, alla richiesta pull deve essere associato un problema</span><span class="sxs-lookup"><span data-stu-id="c3992-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="c3992-125">per cui si rende necessario rinominare o eliminare i file.</span><span class="sxs-lookup"><span data-stu-id="c3992-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="c3992-126">Evitare di mescolare aggiunte o modifiche di file a ridenominazioni ed eliminazioni.</span><span class="sxs-lookup"><span data-stu-id="c3992-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="c3992-127">Qualsiasi file rinominato o eliminato deve essere aggiunto al file di reindirizzamento principale.</span><span class="sxs-lookup"><span data-stu-id="c3992-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="c3992-128">Se possibile, è anche opportuno aggiornare i file collegati al contenuto rinominato o eliminato.</span><span class="sxs-lookup"><span data-stu-id="c3992-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="c3992-129">Questo riguarda anche i file di sommario.</span><span class="sxs-lookup"><span data-stu-id="c3992-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="c3992-130">Servizio di convalida delle richieste pull di documenti</span><span class="sxs-lookup"><span data-stu-id="c3992-130">Docs PR validation service</span></span>

<span data-ttu-id="c3992-131">In GitHub è disponibile l'app Docs PR che esegue le regole di convalida sui file di una richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="c3992-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="c3992-132">È necessario correggere eventuali errori o avvisi (vedere le eccezioni) segnalati dal servizio di convalida.</span><span class="sxs-lookup"><span data-stu-id="c3992-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="c3992-133">È possibile ignorare gli avvisi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c3992-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="c3992-134">Verrà visualizzato questo comportamento:</span><span class="sxs-lookup"><span data-stu-id="c3992-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="c3992-135">Si invia una richiesta pull.</span><span class="sxs-lookup"><span data-stu-id="c3992-135">You submit a PR.</span></span>
1. <span data-ttu-id="c3992-136">Nel commento di GitHub che indica lo stato della richiesta pull viene visualizzato lo stato di "controllo" abilitato per il repository.</span><span class="sxs-lookup"><span data-stu-id="c3992-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repo.</span></span> <span data-ttu-id="c3992-137">Si noti che in questo esempio sono abilitati due controlli, "Commit Validation" e "OpenPublishing.Build":</span><span class="sxs-lookup"><span data-stu-id="c3992-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![alcuni controlli non sono riusciti](media/pull-requests/validation-failed.png)

   <span data-ttu-id="c3992-139">La compilazione può essere passata anche se la convalida del commit ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="c3992-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="c3992-140">Per altre informazioni, vedere i **dettagli**.</span><span class="sxs-lookup"><span data-stu-id="c3992-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="c3992-141">Nella pagina dei dettagli sono visualizzati tutti i controlli di convalida non riusciti, con informazioni su come risolvere i problemi.</span><span class="sxs-lookup"><span data-stu-id="c3992-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="c3992-142">Quando la convalida ha esito positivo, alla richiesta pull viene aggiunto il seguente commento:</span><span class="sxs-lookup"><span data-stu-id="c3992-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![convalida della compilazione](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="c3992-144">Se si è un collaboratore esterno, non un dipendente Microsoft, non si ha accesso ai report di compilazione dettagliati o ai collegamenti all'anteprima.</span><span class="sxs-lookup"><span data-stu-id="c3992-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="c3992-145">Quando la richiesta pull viene esaminata da un membro del team di PowerShell-Docs, può essere necessario apportare modifiche o risolvere i problemi contrassegnati dal report di convalida.</span><span class="sxs-lookup"><span data-stu-id="c3992-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="c3992-146">Il team di PowerShell-Docs può aiutare l'utente a capire come correggere ed evitare questi problemi negli invii futuri.</span><span class="sxs-lookup"><span data-stu-id="c3992-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c3992-147">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="c3992-147">Next steps</span></span>

[<span data-ttu-id="c3992-148">Guida di stile per la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3992-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="c3992-149">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="c3992-149">Additional resources</span></span>

[<span data-ttu-id="c3992-150">Modalità di gestione delle richieste pull</span><span class="sxs-lookup"><span data-stu-id="c3992-150">How we manage pull requests</span></span>](managing-pull-requests.md)
