---
title: Ciclo di vita del supporto di PowerShell Core
description: Criteri che disciplinano il supporto per PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: cb1daf953b11ffba8f39bcc05a8b122350c497eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682959"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="bc4c7-103">Ciclo di vita del supporto di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="bc4c7-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="bc4c7-104">PowerShell Core è un set distinto di strumenti e componenti che viene fornito, installato e configurato separatamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="bc4c7-105">Pertanto, PowerShell Core non è incluso in Windows 7/8.1/10 o Windows Server al contratto di licenza.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="bc4c7-106">PowerShell Core è tuttavia supportato nei contratti di supporto Microsoft tradizionali, tra cui [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="bc4c7-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="bc4c7-107">È anche possibile acquistare il [supporto assistito][] per PowerShell Core inviando una richiesta di supporto per il problema riscontrato.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="bc4c7-108">È inoltre disponibile il [supporto della community][] in GitHub dove è possibile segnalare un problema o un bug oppure inviare una richiesta di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="bc4c7-109">Inoltre, è possibile ricevere assistenza da altri membri della community nella pagina Generale [Microsoft Community][] o il Microsoft [PowerShell Tech Community][].</span><span class="sxs-lookup"><span data-stu-id="bc4c7-109">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="bc4c7-110">Microsoft non ci sono garanzie che la community verrà indirizzo o di risolvere il problema in modo tempestivo.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-110">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="bc4c7-111">Nel caso di un problema che richieda attenzione immediata è consigliabile usare le tradizionali opzioni di supporto a pagamento.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="bc4c7-112">Ciclo di vita di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="bc4c7-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="bc4c7-113">PowerShell Core adotta i [Criteri moderni Microsoft relativi al ciclo di vita][modern].</span><span class="sxs-lookup"><span data-stu-id="bc4c7-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="bc4c7-114">Questo ciclo di vita del supporto è stato pensato per mantenere i clienti sempre aggiornati con le versioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="bc4c7-115">Il ramo della versione 6.x di PowerShell Core verrà aggiornato approssimativamente ogni sei mesi (esempi: 6.0, 6.1, 6.2, ecc.)</span><span class="sxs-lookup"><span data-stu-id="bc4c7-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc4c7-116">Per continuare a ricevere il supporto è necessario eseguire l'aggiornamento entro sei mesi dal rilascio di ogni nuova versione secondaria.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="bc4c7-117">Ad esempio, se PowerShell Core 6.1 viene rilasciato il 1 ° luglio 2018, dovrebbe eseguire l'aggiornamento a PowerShell Core 6.1 dal 1 ° gennaio 2019 per mantenere il supporto tecnico.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-117">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

![Ciclo di vita del ramo PowerShell Core][lifecycle-chart]

<span data-ttu-id="bc4c7-119">I criteri del ciclo di vita moderni richiede inoltre che Microsoft offrire ai clienti preavviso di 12 mesi prima di sospendere il supporto per un prodotto (vale a dire, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="bc4c7-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="bc4c7-120">Infine, prevediamo di PowerShell Core verrà adottato il "Long Term servicing" approccio.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="bc4c7-121">Questo approccio per la manutenzione, richiede solo per la manutenzione e aggiornamenti della protezione al supporto per una determinato ramo/versione di 6.x.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-121">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="bc4c7-122">Piattaforme supportate</span><span class="sxs-lookup"><span data-stu-id="bc4c7-122">Supported platforms</span></span>

<span data-ttu-id="bc4c7-123">Nella tabella seguente per visualizzare la versione di PowerShell Core si usa la piattaforma è ufficialmente supportata.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-123">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="bc4c7-124">La nostra community ha anche reso disponibili pacchetti per alcune piattaforme, ma non sono ufficialmente supportati.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-124">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="bc4c7-125">Questi pacchetti sono contrassegnati come `Community` nella tabella.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-125">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="bc4c7-126">Le piattaforme elencate come `Experimental` non sono ufficialmente supportate, ma sono disponibili per la sperimentazione e per l'invio di commenti e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-126">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="bc4c7-127">6.0</span><span class="sxs-lookup"><span data-stu-id="bc4c7-127">6.0</span></span>         | <span data-ttu-id="bc4c7-128">6.1</span><span class="sxs-lookup"><span data-stu-id="bc4c7-128">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="bc4c7-129">Windows 7, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="bc4c7-129">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="bc4c7-130">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-130">Supported</span></span>   | <span data-ttu-id="bc4c7-131">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-131">Supported</span></span>   |
| <span data-ttu-id="bc4c7-132">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="bc4c7-132">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="bc4c7-133">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-133">Supported</span></span>   | <span data-ttu-id="bc4c7-134">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-134">Supported</span></span>   |
| <span data-ttu-id="bc4c7-135">[Canale semestrale di Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="bc4c7-135">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="bc4c7-136">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-136">Supported</span></span>   | <span data-ttu-id="bc4c7-137">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-137">Supported</span></span>   |
| <span data-ttu-id="bc4c7-138">Ubuntu 14.04 e 16.04</span><span class="sxs-lookup"><span data-stu-id="bc4c7-138">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="bc4c7-139">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-139">Supported</span></span>   | <span data-ttu-id="bc4c7-140">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-140">Supported</span></span>   |
| <span data-ttu-id="bc4c7-141">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="bc4c7-141">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="bc4c7-142">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-142">Supported</span></span>   |
| <span data-ttu-id="bc4c7-143">Ubuntu 18.10 (tramite pacchetto Snap)</span><span class="sxs-lookup"><span data-stu-id="bc4c7-143">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="bc4c7-144">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-144">Community</span></span>   |
| <span data-ttu-id="bc4c7-145">Debian 9</span><span class="sxs-lookup"><span data-stu-id="bc4c7-145">Debian 9</span></span>                                          | <span data-ttu-id="bc4c7-146">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-146">Supported</span></span>   | <span data-ttu-id="bc4c7-147">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-147">Supported</span></span>   |
| <span data-ttu-id="bc4c7-148">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bc4c7-148">CentOS 7</span></span>                                          | <span data-ttu-id="bc4c7-149">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-149">Supported</span></span>   | <span data-ttu-id="bc4c7-150">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-150">Supported</span></span>   |
| <span data-ttu-id="bc4c7-151">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bc4c7-151">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="bc4c7-152">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-152">Supported</span></span>   | <span data-ttu-id="bc4c7-153">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-153">Supported</span></span>   |
| <span data-ttu-id="bc4c7-154">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="bc4c7-154">openSUSE 42.3</span></span>                                     | <span data-ttu-id="bc4c7-155">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-155">Supported</span></span>   | <span data-ttu-id="bc4c7-156">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-156">Supported</span></span>   |
| <span data-ttu-id="bc4c7-157">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="bc4c7-157">Fedora 28</span></span>                                         |             | <span data-ttu-id="bc4c7-158">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-158">Supported</span></span>   |
| <span data-ttu-id="bc4c7-159">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="bc4c7-159">macOS 10.12+</span></span>                                      | <span data-ttu-id="bc4c7-160">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-160">Supported</span></span>   | <span data-ttu-id="bc4c7-161">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="bc4c7-161">Supported</span></span>   |
| <span data-ttu-id="bc4c7-162">Arch</span><span class="sxs-lookup"><span data-stu-id="bc4c7-162">Arch</span></span>                                              | <span data-ttu-id="bc4c7-163">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-163">Community</span></span>   | <span data-ttu-id="bc4c7-164">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-164">Community</span></span>   |
| <span data-ttu-id="bc4c7-165">Raspbian</span><span class="sxs-lookup"><span data-stu-id="bc4c7-165">Raspbian</span></span>                                          | <span data-ttu-id="bc4c7-166">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="bc4c7-166">Experimental</span></span>| <span data-ttu-id="bc4c7-167">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-167">Community</span></span>   |
| <span data-ttu-id="bc4c7-168">Kali</span><span class="sxs-lookup"><span data-stu-id="bc4c7-168">Kali</span></span>                                              | <span data-ttu-id="bc4c7-169">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-169">Community</span></span>   | <span data-ttu-id="bc4c7-170">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-170">Community</span></span>   |
| <span data-ttu-id="bc4c7-171">AppImage (funziona su più piattaforme Linux)</span><span class="sxs-lookup"><span data-stu-id="bc4c7-171">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="bc4c7-172">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-172">Community</span></span>   | <span data-ttu-id="bc4c7-173">Community</span><span class="sxs-lookup"><span data-stu-id="bc4c7-173">Community</span></span>   |
| [<span data-ttu-id="bc4c7-174">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="bc4c7-174">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="bc4c7-175">Vedere la nota</span><span class="sxs-lookup"><span data-stu-id="bc4c7-175">See note</span></span>    | <span data-ttu-id="bc4c7-176">Vedere la nota</span><span class="sxs-lookup"><span data-stu-id="bc4c7-176">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="bc4c7-177">I pacchetti Snap saranno sperimentali per un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-177">Snap packages will be experimental for a period.</span></span>
> <span data-ttu-id="bc4c7-178">Successivamente, se come previsto Snap non introdurrà nuovi problemi di supporto, il supporto seguirà la distribuzione in cui è in esecuzione il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-178">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="bc4c7-179">PowerShell versione finale del ciclo di vita</span><span class="sxs-lookup"><span data-stu-id="bc4c7-179">PowerShell release end of life</span></span>

<span data-ttu-id="bc4c7-180">In base [ciclo di vita di PowerShell Core](#lifecycle-of-powershell-core), la tabella seguente elenca le date quando vari versione verrà non più supportato.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-180">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="bc4c7-181">Versione</span><span class="sxs-lookup"><span data-stu-id="bc4c7-181">Version</span></span> | <span data-ttu-id="bc4c7-182">Fine vita</span><span class="sxs-lookup"><span data-stu-id="bc4c7-182">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="bc4c7-183">6.0</span><span class="sxs-lookup"><span data-stu-id="bc4c7-183">6.0</span></span>     | <span data-ttu-id="bc4c7-184">13 febbraio 2019</span><span class="sxs-lookup"><span data-stu-id="bc4c7-184">February 13, 2019</span></span>             |
| <span data-ttu-id="bc4c7-185">6.1</span><span class="sxs-lookup"><span data-stu-id="bc4c7-185">6.1</span></span>     | <span data-ttu-id="bc4c7-186">6 mesi dopo la 6.2 Release</span><span class="sxs-lookup"><span data-stu-id="bc4c7-186">6 Months after 6.2 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="bc4c7-187">Piattaforme, non supportati</span><span class="sxs-lookup"><span data-stu-id="bc4c7-187">Platforms, which are out of support</span></span>

<span data-ttu-id="bc4c7-188">Quando una versione della piattaforma raggiunge la fine del ciclo di vita come definito dal proprietario della piattaforma, PowerShell Core cesserà anche supportare tale versione della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-188">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="bc4c7-189">I pacchetti rilasciati in precedenza rimarranno disponibili per i clienti che devono accedervi, ma non verranno più forniti il supporto formale e gli aggiornamenti di qualsiasi tipo.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-189">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="bc4c7-190">Pertanto, i proprietari di distribuzione è terminato il supporto per le seguenti versioni e non sono supportati.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-190">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="bc4c7-191">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="bc4c7-191">OS</span></span>       | <span data-ttu-id="bc4c7-192">Versione</span><span class="sxs-lookup"><span data-stu-id="bc4c7-192">Version</span></span> | <span data-ttu-id="bc4c7-193">Fine vita</span><span class="sxs-lookup"><span data-stu-id="bc4c7-193">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="bc4c7-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="bc4c7-194">Fedora</span></span>   | <span data-ttu-id="bc4c7-195">24</span><span class="sxs-lookup"><span data-stu-id="bc4c7-195">24</span></span>      | [<span data-ttu-id="bc4c7-196">Agosto 2017</span><span class="sxs-lookup"><span data-stu-id="bc4c7-196">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="bc4c7-197">Fedora</span><span class="sxs-lookup"><span data-stu-id="bc4c7-197">Fedora</span></span>   | <span data-ttu-id="bc4c7-198">25</span><span class="sxs-lookup"><span data-stu-id="bc4c7-198">25</span></span>      | [<span data-ttu-id="bc4c7-199">Dicembre 2017</span><span class="sxs-lookup"><span data-stu-id="bc4c7-199">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="bc4c7-200">Fedora</span><span class="sxs-lookup"><span data-stu-id="bc4c7-200">Fedora</span></span>   | <span data-ttu-id="bc4c7-201">26</span><span class="sxs-lookup"><span data-stu-id="bc4c7-201">26</span></span>      | [<span data-ttu-id="bc4c7-202">Maggio 2018</span><span class="sxs-lookup"><span data-stu-id="bc4c7-202">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="bc4c7-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="bc4c7-203">openSUSE</span></span> | <span data-ttu-id="bc4c7-204">42.1</span><span class="sxs-lookup"><span data-stu-id="bc4c7-204">42.1</span></span>    | [<span data-ttu-id="bc4c7-205">Maggio 2017</span><span class="sxs-lookup"><span data-stu-id="bc4c7-205">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="bc4c7-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="bc4c7-206">openSUSE</span></span> | <span data-ttu-id="bc4c7-207">42.2</span><span class="sxs-lookup"><span data-stu-id="bc4c7-207">42.2</span></span>    | [<span data-ttu-id="bc4c7-208">Gennaio 2018</span><span class="sxs-lookup"><span data-stu-id="bc4c7-208">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="bc4c7-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bc4c7-209">Ubuntu</span></span>   | <span data-ttu-id="bc4c7-210">16.10</span><span class="sxs-lookup"><span data-stu-id="bc4c7-210">16.10</span></span>   | [<span data-ttu-id="bc4c7-211">Luglio 2017</span><span class="sxs-lookup"><span data-stu-id="bc4c7-211">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="bc4c7-212">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bc4c7-212">Ubuntu</span></span>   | <span data-ttu-id="bc4c7-213">17.04</span><span class="sxs-lookup"><span data-stu-id="bc4c7-213">17.04</span></span>   | [<span data-ttu-id="bc4c7-214">Gennaio 2018</span><span class="sxs-lookup"><span data-stu-id="bc4c7-214">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="bc4c7-215">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bc4c7-215">Ubuntu</span></span>   | <span data-ttu-id="bc4c7-216">17.10</span><span class="sxs-lookup"><span data-stu-id="bc4c7-216">17.10</span></span>   | [<span data-ttu-id="bc4c7-217">Luglio 2018</span><span class="sxs-lookup"><span data-stu-id="bc4c7-217">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="bc4c7-218">Debian</span><span class="sxs-lookup"><span data-stu-id="bc4c7-218">Debian</span></span>   | <span data-ttu-id="bc4c7-219">8</span><span class="sxs-lookup"><span data-stu-id="bc4c7-219">8</span></span>       | [<span data-ttu-id="bc4c7-220">Giugno 2018</span><span class="sxs-lookup"><span data-stu-id="bc4c7-220">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="bc4c7-221">Fedora</span><span class="sxs-lookup"><span data-stu-id="bc4c7-221">Fedora</span></span>   | <span data-ttu-id="bc4c7-222">27</span><span class="sxs-lookup"><span data-stu-id="bc4c7-222">27</span></span>      | [<span data-ttu-id="bc4c7-223">Novembre 2018</span><span class="sxs-lookup"><span data-stu-id="bc4c7-223">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |

## <a name="notes-on-licensing"></a><span data-ttu-id="bc4c7-224">Note sulla licenza</span><span class="sxs-lookup"><span data-stu-id="bc4c7-224">Notes on licensing</span></span>

<span data-ttu-id="bc4c7-225">PowerShell Core viene rilasciato con la [licenza MIT][].</span><span class="sxs-lookup"><span data-stu-id="bc4c7-225">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="bc4c7-226">Condizioni della presente licenza e senza un contratto di supporto a pagamento, gli utenti non possono superare [supporto della community][].</span><span class="sxs-lookup"><span data-stu-id="bc4c7-226">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="bc4c7-227">Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-227">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="bc4c7-228">Modulo Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc4c7-228">Windows PowerShell Module</span></span>

<span data-ttu-id="bc4c7-229">Supporto per PowerShell Core non include i moduli di prodotto, a meno che tali moduli supportano in modo esplicito PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-229">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="bc4c7-230">Ad esempio, l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è uno scenario non supportato.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-230">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="bc4c7-231">Tuttavia, i moduli che non supportano in modo esplicito PowerShell Core possono essere compatibili in alcuni casi.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-231">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="bc4c7-232">Installando i [ `WindowsPSModulePath` ][] modulo, è possibile aggiungere il comando di Windows PowerShell `PSModulePath` a di PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="bc4c7-232">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="bc4c7-233">Installare prima il modulo `WindowsPSModulePath` da PowerShell Gallery:</span><span class="sxs-lookup"><span data-stu-id="bc4c7-233">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="bc4c7-234">Dopo l'installazione di questo modulo, eseguire il cmdlet `Add-WindowsPSModulePath` per aggiungere `PSModulePath` di Windows PowerShell a PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="bc4c7-234">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[supporto della community]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[supporto assistito]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licenza MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
