---
ms.date: 08/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Note sulla versione di WMF 5.1
ms.openlocfilehash: 9df21afe52e79dc248871b999afead21f8678d52
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="fc042-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="fc042-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="fc042-104">WMF offre agli utenti la possibilità di aggiornare i sistemi Windows esistenti alle versioni dei componenti PowerShell, WMI, WinRM e Registrazione inventario software (SIL) rilasciati con Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="fc042-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="fc042-105">WMF 5.1 può essere installato in Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e offre alcuni miglioramenti rispetto a WMF 5.0 RTM, tra cui:</span><span class="sxs-lookup"><span data-stu-id="fc042-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="fc042-106">Nuovi cmdlet: utenti locali e gruppi; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="fc042-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="fc042-107">I miglioramenti apportati a PowerShellGet includono l'applicazione di moduli firmati e l'installazione di moduli JEA</span><span class="sxs-lookup"><span data-stu-id="fc042-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="fc042-108">È stato aggiunto il supporto di PackageManagement per i contenitori, l'installazione di CBS, l'installazione basata su EXE e i pacchetti CAB</span><span class="sxs-lookup"><span data-stu-id="fc042-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="fc042-109">Miglioramenti del debug per le classi DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc042-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="fc042-110">Miglioramenti relativi alla sicurezza, incluso quando si usano i cmdlet PowerShellGet e quando si applicano i moduli firmati da catalogo provenienti dal server di pull</span><span class="sxs-lookup"><span data-stu-id="fc042-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="fc042-111">Risposte ad alcune richieste o problemi segnalati da utenti</span><span class="sxs-lookup"><span data-stu-id="fc042-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="fc042-112">Per altre informazioni sulle novità in questa versione, vedere gli argomenti elencati in [Nuovi scenari e funzionalità](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="fc042-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="fc042-113">L'argomento [Installare e configurare](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) elenca i requisiti e include istruzioni per l'installazione di WMF.</span><span class="sxs-lookup"><span data-stu-id="fc042-113">The [Install and Configure](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="fc042-114">L'argomento [Compatibilità](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) elenca quali versioni di WMF possono essere installate in quali versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="fc042-114">The [Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="fc042-115">In [Compatibilità del prodotto](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) sono elencate le applicazioni Microsoft per cui al momento non è approvato l'uso di WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="fc042-115">[Product Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="fc042-116">Le informazioni dettagliate per i componenti di WMF saranno disponibili nella documentazione di MSDN:</span><span class="sxs-lookup"><span data-stu-id="fc042-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="fc042-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fc042-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/en-us/powershell/)
- <span data-ttu-id="fc042-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc042-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="fc042-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc042-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="fc042-120">[Registrazione inventario software](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc042-120">[Software Inventory Logging](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span></span>