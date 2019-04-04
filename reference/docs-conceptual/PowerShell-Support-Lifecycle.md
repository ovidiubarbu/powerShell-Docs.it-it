---
title: Ciclo di vita del supporto di PowerShell Core
description: Criteri che disciplinano il supporto per PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623859"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="86e39-103">Ciclo di vita del supporto di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="86e39-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="86e39-104">PowerShell Core è un set distinto di strumenti e componenti che viene fornito, installato e configurato separatamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86e39-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="86e39-105">PowerShell Core non è pertanto incluso nei contratti di licenza di Windows 7/8.1/10 o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="86e39-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="86e39-106">PowerShell Core è tuttavia supportato nei contratti di supporto Microsoft tradizionali, tra cui [Premier][], [Microsoft Enterprise Agreement][enterprise-agreement] e [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="86e39-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="86e39-107">È anche possibile acquistare il [supporto assistito][] per PowerShell Core inviando una richiesta di supporto per il problema riscontrato.</span><span class="sxs-lookup"><span data-stu-id="86e39-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="86e39-108">Supporto della community</span><span class="sxs-lookup"><span data-stu-id="86e39-108">Community Support</span></span>

<span data-ttu-id="86e39-109">È inoltre disponibile il [supporto della community][] in GitHub dove è possibile segnalare un problema o un bug oppure inviare una richiesta di funzionalità.</span><span class="sxs-lookup"><span data-stu-id="86e39-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="86e39-110">È anche possibile ricevere assistenza da altri membri della community nella pagina generale di [Microsoft Community][] o in Microsoft [PowerShell Tech Community][].</span><span class="sxs-lookup"><span data-stu-id="86e39-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="86e39-111">Microsoft non offre garanzie che il problema verrà affrontato o risolto in modo tempestivo dalla community.</span><span class="sxs-lookup"><span data-stu-id="86e39-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="86e39-112">Nel caso di un problema che richieda attenzione immediata è consigliabile usare le tradizionali opzioni di supporto a pagamento.</span><span class="sxs-lookup"><span data-stu-id="86e39-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="86e39-113">Ciclo di vita di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="86e39-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="86e39-114">PowerShell Core adotta i [Criteri moderni Microsoft relativi al ciclo di vita][modern].</span><span class="sxs-lookup"><span data-stu-id="86e39-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="86e39-115">Questo ciclo di vita del supporto è stato pensato per mantenere i clienti sempre aggiornati con le versioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="86e39-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="86e39-116">Il ramo della versione 6.x di PowerShell Core verrà aggiornato approssimativamente ogni sei mesi (ad esempio, 6.0, 6.1, 6.2 e così via).</span><span class="sxs-lookup"><span data-stu-id="86e39-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86e39-117">Per continuare a ricevere il supporto è necessario eseguire l'aggiornamento entro sei mesi dal rilascio di ogni nuova versione secondaria.</span><span class="sxs-lookup"><span data-stu-id="86e39-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="86e39-118">Ad esempio, se PowerShell Core 6.1 viene rilasciato il 1° luglio 2018, sarà necessario eseguire l'aggiornamento a PowerShell Core 6.1 entro il 1° gennaio 1 2019 per mantenere il supporto.</span><span class="sxs-lookup"><span data-stu-id="86e39-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86e39-119">Per continuare a ricevere il supporto, è necessario eseguire l'aggiornamento entro 30 giorni dal rilascio di ogni nuova versione di patch.</span><span class="sxs-lookup"><span data-stu-id="86e39-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="86e39-120">Ad esempio, se si esegue PowerShell Core 6.1 e la versione 6.1.3 è stata rilasciata il 19 febbraio 2019, per mantenere il supporto occorre eseguire l'aggiornamento a PowerShell Core 6.1.3 entro il 21 marzo 2019, ovvero 30 giorni dopo il rilascio.</span><span class="sxs-lookup"><span data-stu-id="86e39-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="86e39-121">Se vengono trovate correzioni richieste, queste verranno rilasciate nell'aggiornamento cumulativo successivo.</span><span class="sxs-lookup"><span data-stu-id="86e39-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![Ciclo di vita del ramo PowerShell Core][lifecycle-chart]

<span data-ttu-id="86e39-123">Nei Criteri moderni relativi al ciclo di vita viene anche indicato che Microsoft segnalerà ai clienti il termine del supporto per un prodotto (ad esempio, PowerShell Core) con un preavviso di 12 mesi.</span><span class="sxs-lookup"><span data-stu-id="86e39-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="86e39-124">Infine, è previsto che per PowerShell Core verrà adottato l'approccio "Long Term Servicing" (manutenzione a lungo termine).</span><span class="sxs-lookup"><span data-stu-id="86e39-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="86e39-125">Con questo approccio, verranno inclusi nel supporto solo gli aggiornamenti di manutenzione e di sicurezza per un determinato ramo/versione di 6.x.</span><span class="sxs-lookup"><span data-stu-id="86e39-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="86e39-126">Piattaforme supportate</span><span class="sxs-lookup"><span data-stu-id="86e39-126">Supported platforms</span></span>

<span data-ttu-id="86e39-127">Vedere la tabella seguente per scoprire in quale piattaforma è ufficialmente supportata la versione di PowerShell Core in uso.</span><span class="sxs-lookup"><span data-stu-id="86e39-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="86e39-128">La nostra community ha anche reso disponibili pacchetti per alcune piattaforme, ma non sono ufficialmente supportati.</span><span class="sxs-lookup"><span data-stu-id="86e39-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="86e39-129">Questi pacchetti sono contrassegnati come `Community` nella tabella.</span><span class="sxs-lookup"><span data-stu-id="86e39-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="86e39-130">Le piattaforme elencate come `Experimental` non sono ufficialmente supportate, ma sono disponibili per la sperimentazione e per l'invio di commenti e suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="86e39-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="86e39-131">6.1</span><span class="sxs-lookup"><span data-stu-id="86e39-131">6.1</span></span>         | <span data-ttu-id="86e39-132">6.2</span><span class="sxs-lookup"><span data-stu-id="86e39-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="86e39-133">Windows 7, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="86e39-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="86e39-134">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-134">Supported</span></span>   | <span data-ttu-id="86e39-135">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-135">Supported</span></span>   |
| <span data-ttu-id="86e39-136">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="86e39-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="86e39-137">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-137">Supported</span></span>   | <span data-ttu-id="86e39-138">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-138">Supported</span></span>   |
| <span data-ttu-id="86e39-139">[Canale semestrale di Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="86e39-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="86e39-140">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-140">Supported</span></span>   | <span data-ttu-id="86e39-141">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-141">Supported</span></span>   |
| <span data-ttu-id="86e39-142">Ubuntu 16.04 e 18.04</span><span class="sxs-lookup"><span data-stu-id="86e39-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="86e39-143">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-143">Supported</span></span>   | <span data-ttu-id="86e39-144">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-144">Supported</span></span>   |
| <span data-ttu-id="86e39-145">Ubuntu 18.10 (tramite pacchetto Snap)</span><span class="sxs-lookup"><span data-stu-id="86e39-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="86e39-146">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-146">Community</span></span>   | <span data-ttu-id="86e39-147">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-147">Community</span></span>   |
| <span data-ttu-id="86e39-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="86e39-148">Debian 9</span></span>                                          | <span data-ttu-id="86e39-149">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-149">Supported</span></span>   | <span data-ttu-id="86e39-150">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-150">Supported</span></span>   |
| <span data-ttu-id="86e39-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="86e39-151">CentOS 7</span></span>                                          | <span data-ttu-id="86e39-152">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-152">Supported</span></span>   | <span data-ttu-id="86e39-153">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-153">Supported</span></span>   |
| <span data-ttu-id="86e39-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="86e39-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="86e39-155">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-155">Supported</span></span>   | <span data-ttu-id="86e39-156">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-156">Supported</span></span>   |
| <span data-ttu-id="86e39-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="86e39-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="86e39-158">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-158">Supported</span></span>   | <span data-ttu-id="86e39-159">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-159">Supported</span></span>   |
| <span data-ttu-id="86e39-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="86e39-160">Fedora 28</span></span>                                         | <span data-ttu-id="86e39-161">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-161">Supported</span></span>   | <span data-ttu-id="86e39-162">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-162">Supported</span></span>   |
| <span data-ttu-id="86e39-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="86e39-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="86e39-164">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-164">Supported</span></span>   | <span data-ttu-id="86e39-165">Funzionalità supportata</span><span class="sxs-lookup"><span data-stu-id="86e39-165">Supported</span></span>   |
| <span data-ttu-id="86e39-166">Arch</span><span class="sxs-lookup"><span data-stu-id="86e39-166">Arch</span></span>                                              | <span data-ttu-id="86e39-167">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-167">Community</span></span>   | <span data-ttu-id="86e39-168">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-168">Community</span></span>   |
| <span data-ttu-id="86e39-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="86e39-169">Raspbian</span></span>                                          | <span data-ttu-id="86e39-170">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-170">Community</span></span>   | <span data-ttu-id="86e39-171">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-171">Community</span></span>   |
| <span data-ttu-id="86e39-172">Kali</span><span class="sxs-lookup"><span data-stu-id="86e39-172">Kali</span></span>                                              | <span data-ttu-id="86e39-173">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-173">Community</span></span>   | <span data-ttu-id="86e39-174">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-174">Community</span></span>   |
| <span data-ttu-id="86e39-175">AppImage (funziona su più piattaforme Linux)</span><span class="sxs-lookup"><span data-stu-id="86e39-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="86e39-176">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-176">Community</span></span>   | <span data-ttu-id="86e39-177">Community</span><span class="sxs-lookup"><span data-stu-id="86e39-177">Community</span></span>   |
| [<span data-ttu-id="86e39-178">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="86e39-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="86e39-179">Vedere la nota</span><span class="sxs-lookup"><span data-stu-id="86e39-179">See note</span></span>    | <span data-ttu-id="86e39-180">Vedere la nota</span><span class="sxs-lookup"><span data-stu-id="86e39-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="86e39-181">I pacchetti Snap sono supportati come la distribuzione su cui si esegue il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="86e39-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="86e39-182">Fine vita di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86e39-182">PowerShell release end of life</span></span>

<span data-ttu-id="86e39-183">In base al [ciclo di vita di PowerShell Core](#lifecycle-of-powershell-core), la tabella seguente elenca le date in cui non saranno più supportate le varie versioni.</span><span class="sxs-lookup"><span data-stu-id="86e39-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="86e39-184">Versione</span><span class="sxs-lookup"><span data-stu-id="86e39-184">Version</span></span> | <span data-ttu-id="86e39-185">Fine vita</span><span class="sxs-lookup"><span data-stu-id="86e39-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="86e39-186">6.0</span><span class="sxs-lookup"><span data-stu-id="86e39-186">6.0</span></span>     | <span data-ttu-id="86e39-187">13 febbraio 2019</span><span class="sxs-lookup"><span data-stu-id="86e39-187">February 13, 2019</span></span>             |
| <span data-ttu-id="86e39-188">6.1</span><span class="sxs-lookup"><span data-stu-id="86e39-188">6.1</span></span>     | <span data-ttu-id="86e39-189">28 settembre 2019</span><span class="sxs-lookup"><span data-stu-id="86e39-189">September 28, 2019</span></span>            |
| <span data-ttu-id="86e39-190">6.2</span><span class="sxs-lookup"><span data-stu-id="86e39-190">6.2</span></span>     | <span data-ttu-id="86e39-191">6 mesi dopo le versioni 6.3</span><span class="sxs-lookup"><span data-stu-id="86e39-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="86e39-192">Piattaforme non più supportate</span><span class="sxs-lookup"><span data-stu-id="86e39-192">Platforms, which are out of support</span></span>

<span data-ttu-id="86e39-193">Quando una versione di una piattaforma raggiunge la fine del ciclo di vita come definito dal proprietario della piattaforma, anche PowerShell Core interromperà il supporto per tale versione.</span><span class="sxs-lookup"><span data-stu-id="86e39-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="86e39-194">I pacchetti rilasciati in precedenza rimarranno disponibili per i clienti che devono accedervi, ma non verranno più forniti il supporto formale e gli aggiornamenti di qualsiasi tipo.</span><span class="sxs-lookup"><span data-stu-id="86e39-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="86e39-195">Pertanto, il supporto per le versioni seguenti è stato terminato dai proprietari della distribuzione e tali versioni non sono più supportate.</span><span class="sxs-lookup"><span data-stu-id="86e39-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="86e39-196">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="86e39-196">OS</span></span>       | <span data-ttu-id="86e39-197">Versione</span><span class="sxs-lookup"><span data-stu-id="86e39-197">Version</span></span> | <span data-ttu-id="86e39-198">Fine vita</span><span class="sxs-lookup"><span data-stu-id="86e39-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="86e39-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="86e39-199">Fedora</span></span>   | <span data-ttu-id="86e39-200">24</span><span class="sxs-lookup"><span data-stu-id="86e39-200">24</span></span>      | [<span data-ttu-id="86e39-201">Agosto 2017</span><span class="sxs-lookup"><span data-stu-id="86e39-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="86e39-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="86e39-202">Fedora</span></span>   | <span data-ttu-id="86e39-203">25</span><span class="sxs-lookup"><span data-stu-id="86e39-203">25</span></span>      | [<span data-ttu-id="86e39-204">Dicembre 2017</span><span class="sxs-lookup"><span data-stu-id="86e39-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="86e39-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="86e39-205">Fedora</span></span>   | <span data-ttu-id="86e39-206">26</span><span class="sxs-lookup"><span data-stu-id="86e39-206">26</span></span>      | [<span data-ttu-id="86e39-207">Maggio 2018</span><span class="sxs-lookup"><span data-stu-id="86e39-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="86e39-208">openSUSE</span><span class="sxs-lookup"><span data-stu-id="86e39-208">openSUSE</span></span> | <span data-ttu-id="86e39-209">42.1</span><span class="sxs-lookup"><span data-stu-id="86e39-209">42.1</span></span>    | [<span data-ttu-id="86e39-210">Maggio 2017</span><span class="sxs-lookup"><span data-stu-id="86e39-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="86e39-211">openSUSE</span><span class="sxs-lookup"><span data-stu-id="86e39-211">openSUSE</span></span> | <span data-ttu-id="86e39-212">42.2</span><span class="sxs-lookup"><span data-stu-id="86e39-212">42.2</span></span>    | [<span data-ttu-id="86e39-213">Gennaio 2018</span><span class="sxs-lookup"><span data-stu-id="86e39-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="86e39-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86e39-214">Ubuntu</span></span>   | <span data-ttu-id="86e39-215">16.10</span><span class="sxs-lookup"><span data-stu-id="86e39-215">16.10</span></span>   | [<span data-ttu-id="86e39-216">Luglio 2017</span><span class="sxs-lookup"><span data-stu-id="86e39-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="86e39-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86e39-217">Ubuntu</span></span>   | <span data-ttu-id="86e39-218">17.04</span><span class="sxs-lookup"><span data-stu-id="86e39-218">17.04</span></span>   | [<span data-ttu-id="86e39-219">Gennaio 2018</span><span class="sxs-lookup"><span data-stu-id="86e39-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="86e39-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86e39-220">Ubuntu</span></span>   | <span data-ttu-id="86e39-221">17.10</span><span class="sxs-lookup"><span data-stu-id="86e39-221">17.10</span></span>   | [<span data-ttu-id="86e39-222">Luglio 2018</span><span class="sxs-lookup"><span data-stu-id="86e39-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="86e39-223">Debian</span><span class="sxs-lookup"><span data-stu-id="86e39-223">Debian</span></span>   | <span data-ttu-id="86e39-224">8</span><span class="sxs-lookup"><span data-stu-id="86e39-224">8</span></span>       | [<span data-ttu-id="86e39-225">Giugno 2018</span><span class="sxs-lookup"><span data-stu-id="86e39-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="86e39-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="86e39-226">Fedora</span></span>   | <span data-ttu-id="86e39-227">27</span><span class="sxs-lookup"><span data-stu-id="86e39-227">27</span></span>      | [<span data-ttu-id="86e39-228">Novembre 2018</span><span class="sxs-lookup"><span data-stu-id="86e39-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="86e39-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="86e39-229">Ubuntu</span></span>   | <span data-ttu-id="86e39-230">14.04</span><span class="sxs-lookup"><span data-stu-id="86e39-230">14.04</span></span>   | [<span data-ttu-id="86e39-231">Aprile 2019</span><span class="sxs-lookup"><span data-stu-id="86e39-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="86e39-232">Note sulla licenza</span><span class="sxs-lookup"><span data-stu-id="86e39-232">Notes on licensing</span></span>

<span data-ttu-id="86e39-233">PowerShell Core viene rilasciato con la [licenza MIT][].</span><span class="sxs-lookup"><span data-stu-id="86e39-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="86e39-234">In base a questa licenza e in assenza di un contratto di supporto a pagamento, il supporto per gli utenti è limitato al [supporto della community][].</span><span class="sxs-lookup"><span data-stu-id="86e39-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="86e39-235">Con il supporto della community, Microsoft non garantisce velocità di risposta o correzioni.</span><span class="sxs-lookup"><span data-stu-id="86e39-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="86e39-236">Modulo Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="86e39-236">Windows PowerShell Module</span></span>

<span data-ttu-id="86e39-237">Il supporto per PowerShell Core non include altri moduli del prodotto, a meno che questi non supportino in modo esplicito PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="86e39-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="86e39-238">Ad esempio, l'uso del modulo `ActiveDirectory`, incluso in Windows Server, è uno scenario non supportato.</span><span class="sxs-lookup"><span data-stu-id="86e39-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="86e39-239">Tuttavia, i moduli che non supportano in modo esplicito PowerShell Core possono essere compatibili in alcuni casi.</span><span class="sxs-lookup"><span data-stu-id="86e39-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="86e39-240">Installando il modulo [`WindowsPSModulePath`][] è possibile aggiungere `PSModulePath` di Windows PowerShell a `PSModulePath` di PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="86e39-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="86e39-241">Installare prima il modulo `WindowsPSModulePath` da PowerShell Gallery:</span><span class="sxs-lookup"><span data-stu-id="86e39-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="86e39-242">Dopo l'installazione di questo modulo, eseguire il cmdlet `Add-WindowsPSModulePath` per aggiungere `PSModulePath` di Windows PowerShell a PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="86e39-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="86e39-243">Funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="86e39-243">Experimental features</span></span>

<span data-ttu-id="86e39-244">Le [funzionalità sperimentali][] sono limitate al [supporto della community](#community-support).</span><span class="sxs-lookup"><span data-stu-id="86e39-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
[Funzionalità sperimentali]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
