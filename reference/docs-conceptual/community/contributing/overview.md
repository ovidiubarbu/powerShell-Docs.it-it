---
title: Contributi alla documentazione di PowerShell
description: Questo articolo offre una panoramica su come contribuire alla documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 5db78ae2805cb26aa79aa698cfb8b5d8ba8911dc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402628"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="a4524-103">Contributi alla documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4524-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="a4524-104">Grazie per il supporto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4524-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="a4524-105">La Guida per i collaboratori è una raccolta di articoli che illustrano gli strumenti e i processi usati per creare la documentazione Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4524-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="a4524-106">Alcuni articoli includono informazioni comuni a qualsiasi set di documentazione pubblicato per [docs.microsoft.com][docs].</span><span class="sxs-lookup"><span data-stu-id="a4524-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="a4524-107">Altri sono specifici per la creazione di documentazione per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4524-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="a4524-108">Gli articoli comuni sono disponibili nella [Guida per i collaboratori][contribute] centralizzata.</span><span class="sxs-lookup"><span data-stu-id="a4524-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="a4524-109">Gli articoli specifici per PowerShell sono disponibili qui.</span><span class="sxs-lookup"><span data-stu-id="a4524-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="a4524-110">Come fornire il proprio contributo</span><span class="sxs-lookup"><span data-stu-id="a4524-110">Ways to contribute</span></span>

<span data-ttu-id="a4524-111">È possibile contribuire in due modi.</span><span class="sxs-lookup"><span data-stu-id="a4524-111">There are two ways to contribute.</span></span> <span data-ttu-id="a4524-112">Entrambi i tipi di contributi sono utili per Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4524-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="a4524-113">La [segnalazione di problemi][file-an-issue] consente di identificare gli errori e le lacune nella documentazione.</span><span class="sxs-lookup"><span data-stu-id="a4524-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="a4524-114">A volte i problemi sono difficili da risolvere e richiedono ulteriori indagini e ricerche.</span><span class="sxs-lookup"><span data-stu-id="a4524-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="a4524-115">Il processo di risoluzione favorisce uno scambio di informazioni sul problema e lo sviluppo di una soluzione soddisfacente.</span><span class="sxs-lookup"><span data-stu-id="a4524-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="a4524-116">L'inoltro di nuovi contenuti o modifiche agli articoli esistenti è un processo più impegnativo.</span><span class="sxs-lookup"><span data-stu-id="a4524-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="a4524-117">Le informazioni seguenti definiscono gli strumenti, i processi e gli standard per l'invio di contenuto alla documentazione.</span><span class="sxs-lookup"><span data-stu-id="a4524-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="a4524-118">Prepararsi per creare un contributo</span><span class="sxs-lookup"><span data-stu-id="a4524-118">Prepare to make a contribution</span></span>

<span data-ttu-id="a4524-119">La collaborazione alla documentazione richiede un account GitHub.</span><span class="sxs-lookup"><span data-stu-id="a4524-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="a4524-120">Usare l'elenco di controllo seguente per ottenere gli strumenti e comprendere i processi usati per la creazione di contributi.</span><span class="sxs-lookup"><span data-stu-id="a4524-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. [<span data-ttu-id="a4524-121">Registrarsi a GitHub</span><span class="sxs-lookup"><span data-stu-id="a4524-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="a4524-122">Installare gli strumenti Git e Markdown</span><span class="sxs-lookup"><span data-stu-id="a4524-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="a4524-123">Installare Docs Authoring Pack</span><span class="sxs-lookup"><span data-stu-id="a4524-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="a4524-124">[Installare Posh-Git][posh-git] (non obbligatorio ma consigliato)</span><span class="sxs-lookup"><span data-stu-id="a4524-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="a4524-125">Configurare un repository Git locale</span><span class="sxs-lookup"><span data-stu-id="a4524-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="a4524-126">Esaminare le nozioni fondamentali su Git e GitHub</span><span class="sxs-lookup"><span data-stu-id="a4524-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="a4524-127">Introduzione alla scrittura della documentazione</span><span class="sxs-lookup"><span data-stu-id="a4524-127">Get started writing docs</span></span>

<span data-ttu-id="a4524-128">Esistono due modi per contribuire alle modifiche alla documentazione:</span><span class="sxs-lookup"><span data-stu-id="a4524-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="a4524-129">Modifiche rapide a documenti esistenti</span><span class="sxs-lookup"><span data-stu-id="a4524-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="a4524-130">Correzioni minime, correzione di errori di digitazione o aggiunte di piccole entità</span><span class="sxs-lookup"><span data-stu-id="a4524-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="a4524-131">Flusso di lavoro GitHub completo per la documentazione</span><span class="sxs-lookup"><span data-stu-id="a4524-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="a4524-132">Modifiche importanti, più versioni, aggiunta o modifica di immagini, aggiunta di nuovi articoli</span><span class="sxs-lookup"><span data-stu-id="a4524-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="a4524-133">Leggere anche la sezione [Informazioni di base per la scrittura](/contribute/style-quick-start) della Guida per i collaboratori centralizzata.</span><span class="sxs-lookup"><span data-stu-id="a4524-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="a4524-134">Un'altra ottima risorsa è la [Microsoft Writing Style Guide][style-guide] (Guida allo stile di scrittura Microsoft).</span><span class="sxs-lookup"><span data-stu-id="a4524-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="a4524-135">L'obiettivo della Microsoft Writing Style Guide è aiutare gli editor, i redattori tecnici, gli sviluppatori, gli esperti di marketing e gli altri utenti IT a creare contenuti migliori.</span><span class="sxs-lookup"><span data-stu-id="a4524-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="a4524-136">Le correzioni secondarie o i chiarimenti per la documentazione e gli esempi di codice nei repository pubblici sono coperti dalle [Condizioni per l'utilizzo][terms-of-use] di docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="a4524-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="a4524-137">Usare il flusso di lavoro GitHub completo quando si apportano modifiche significative.</span><span class="sxs-lookup"><span data-stu-id="a4524-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="a4524-138">Se non si è un dipendente di Microsoft, le modifiche significative generano un commento nella richiesta pull che chiede di inoltrare un [contratto di licenza per i contributi (CLA)][cla] online.</span><span class="sxs-lookup"><span data-stu-id="a4524-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="a4524-139">Prima che la richiesta pull venga esaminata o accettata, è necessario completare il modulo online.</span><span class="sxs-lookup"><span data-stu-id="a4524-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="a4524-140">Codice di comportamento</span><span class="sxs-lookup"><span data-stu-id="a4524-140">Code of conduct</span></span>

<span data-ttu-id="a4524-141">Tutti i repository che pubblicano in docs.microsoft.com adottano il [Codice di comportamento Microsoft Open Source](https://opensource.microsoft.com/codeofconduct/) o il [ Codice di comportamento di .NET Foundation](https://dotnetfoundation.org/code-of-conduct).</span><span class="sxs-lookup"><span data-stu-id="a4524-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="a4524-142">Per altre informazioni, vedere le [domande frequenti sul Codice di comportamento](https://opensource.microsoft.com/codeofconduct/faq/).</span><span class="sxs-lookup"><span data-stu-id="a4524-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4524-143">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="a4524-143">Next steps</span></span>

<span data-ttu-id="a4524-144">Gli articoli seguenti illustrano informazioni specifiche per la documentazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4524-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="a4524-145">In caso di sovrapposizioni con le linee guida della Guida per i collaboratori centralizzata, vengono segnalate le differenze tra tali linee guida e il contenuto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4524-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="a4524-146">Vedere i documenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="a4524-146">Review the following documents:</span></span>

- [<span data-ttu-id="a4524-147">Come registrare un problema</span><span class="sxs-lookup"><span data-stu-id="a4524-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="a4524-148">Introduzione alla scrittura della documentazione</span><span class="sxs-lookup"><span data-stu-id="a4524-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="a4524-149">Invio di una richiesta pull</span><span class="sxs-lookup"><span data-stu-id="a4524-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="a4524-150">Guida di stile per la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4524-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="a4524-151">Modifica delle informazioni di riferimento sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="a4524-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="a4524-152">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a4524-152">Additional resources</span></span>

- [<span data-ttu-id="a4524-153">Elenco di controllo editoriale</span><span class="sxs-lookup"><span data-stu-id="a4524-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="a4524-154">Modalità di gestione dei problemi</span><span class="sxs-lookup"><span data-stu-id="a4524-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="a4524-155">Modalità di gestione delle richieste pull</span><span class="sxs-lookup"><span data-stu-id="a4524-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: https://docs.microsoft.com/powershell
[style-guide]: https://docs.microsoft.com/style-guide/welcome/
[terms-of-use]: https://docs.microsoft.com/legal/termsofuse