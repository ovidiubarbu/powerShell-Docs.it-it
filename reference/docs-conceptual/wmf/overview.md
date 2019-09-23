---
ms.date: 04/19/2019
keywords: wmf,powershell,installazione
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147911"
---
# <a name="windows-management-framework"></a><span data-ttu-id="cf544-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="cf544-103">Windows Management Framework</span></span>

<span data-ttu-id="cf544-104">Windows Management Framework (WMF) offre un'interfaccia di gestione coerente per Windows.</span><span class="sxs-lookup"><span data-stu-id="cf544-104">Windows Management Framework (WMF) provides a consistent management interface for Windows.</span></span> <span data-ttu-id="cf544-105">WMF offre un modo semplice per gestire diverse versioni di client Windows e Windows Server.</span><span class="sxs-lookup"><span data-stu-id="cf544-105">WMF provides a seamless way to manage various versions of Windows client and Windows Server.</span></span> <span data-ttu-id="cf544-106">I pacchetti di installazione WMF contengono aggiornamenti alla funzionalità di gestione e sono disponibili per le versioni precedenti di Windows.</span><span class="sxs-lookup"><span data-stu-id="cf544-106">WMF installer packages contain updates to management functionality and are available for older versions of Windows.</span></span>

<span data-ttu-id="cf544-107">L'installazione di WMF aggiunge e/o aggiorna le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="cf544-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="cf544-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf544-108">Windows PowerShell</span></span>
- <span data-ttu-id="cf544-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="cf544-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="cf544-110">Windows PowerShell Integrated Script Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="cf544-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="cf544-111">Gestione remota Windows (WinRM)</span><span class="sxs-lookup"><span data-stu-id="cf544-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="cf544-112">Strumentazione gestione Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="cf544-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="cf544-113">Servizi Web di Windows PowerShell (estensione IIS OData di gestione)</span><span class="sxs-lookup"><span data-stu-id="cf544-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="cf544-114">Registrazione inventario software (SIL)</span><span class="sxs-lookup"><span data-stu-id="cf544-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="cf544-115">Provider CIM di gestione del server</span><span class="sxs-lookup"><span data-stu-id="cf544-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="cf544-116">Note sulla versione di WMF</span><span class="sxs-lookup"><span data-stu-id="cf544-116">WMF Release Notes</span></span>

<span data-ttu-id="cf544-117">Per informazioni sui vari miglioramenti in PowerShell e altri componenti di una determinata versione di WMF, consultare i collegamenti seguenti per rivedere le note sulla versione:</span><span class="sxs-lookup"><span data-stu-id="cf544-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>

- [<span data-ttu-id="cf544-118">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="cf544-118">WMF 5.1</span></span>](whats-new/release-notes.md#wmf-51-changes)
- [<span data-ttu-id="cf544-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="cf544-119">WMF 5.0</span></span>](whats-new/release-notes.md#wmf-50-changes)
- [<span data-ttu-id="cf544-120">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="cf544-120">WMF 4.0</span></span>](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [<span data-ttu-id="cf544-121">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="cf544-121">WMF 3.0</span></span>](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="cf544-122">Disponibilità di WMF tra i sistemi operativi Windows</span><span class="sxs-lookup"><span data-stu-id="cf544-122">WMF Availability Across Windows Operating Systems</span></span>

|        <span data-ttu-id="cf544-123">Versione del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="cf544-123">Operating System Version</span></span>         | <span data-ttu-id="cf544-124">[WMF 5.1][]</span><span class="sxs-lookup"><span data-stu-id="cf544-124">[WMF 5.1][]</span></span>  | <span data-ttu-id="cf544-125">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="cf544-125">WMF 5.0</span></span><br><span data-ttu-id="cf544-126">*Supporto scaduto*</span><span class="sxs-lookup"><span data-stu-id="cf544-126">*Out of support*</span></span> | <span data-ttu-id="cf544-127">[WMF 4.0][]</span><span class="sxs-lookup"><span data-stu-id="cf544-127">[WMF 4.0][]</span></span>  | <span data-ttu-id="cf544-128">[WMF 3.0][]</span><span class="sxs-lookup"><span data-stu-id="cf544-128">[WMF 3.0][]</span></span>  | <span data-ttu-id="cf544-129">[WMF 2.0][]</span><span class="sxs-lookup"><span data-stu-id="cf544-129">[WMF 2.0][]</span></span>  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| <span data-ttu-id="cf544-130">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="cf544-130">Windows Server 2019</span></span>                     | <span data-ttu-id="cf544-131">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-131">Ships in-box</span></span> |                             |              |              |              |
| <span data-ttu-id="cf544-132">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="cf544-132">Windows Server 2016</span></span>                     | <span data-ttu-id="cf544-133">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-133">Ships in-box</span></span> |                             |              |              |              |
| <span data-ttu-id="cf544-134">Windows 10</span><span class="sxs-lookup"><span data-stu-id="cf544-134">Windows 10</span></span>                              | <span data-ttu-id="cf544-135">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-135">Ships in-box</span></span> | <span data-ttu-id="cf544-136">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-136">Ships in-box</span></span>                |              |              |              |
| <span data-ttu-id="cf544-137">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="cf544-137">Windows Server 2012 R2</span></span>                  | <span data-ttu-id="cf544-138">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-138">Yes</span></span>          | <span data-ttu-id="cf544-139">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-139">Yes</span></span>                         | <span data-ttu-id="cf544-140">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-140">Ships in-box</span></span> |              |              |
| <span data-ttu-id="cf544-141">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cf544-141">Windows 8.1</span></span>                             | <span data-ttu-id="cf544-142">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-142">Yes</span></span>          | <span data-ttu-id="cf544-143">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-143">Yes</span></span>                         | <span data-ttu-id="cf544-144">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-144">Ships in-box</span></span> |              |              |
| <span data-ttu-id="cf544-145">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="cf544-145">Windows Server 2012</span></span>                     | <span data-ttu-id="cf544-146">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-146">Yes</span></span>          | <span data-ttu-id="cf544-147">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-147">Yes</span></span>                         | <span data-ttu-id="cf544-148">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-148">Yes</span></span>          | <span data-ttu-id="cf544-149">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-149">Ships in-box</span></span> |              |
| <span data-ttu-id="cf544-150">Windows 8</span><span class="sxs-lookup"><span data-stu-id="cf544-150">Windows 8</span></span><br><span data-ttu-id="cf544-151">*Supporto scaduto*</span><span class="sxs-lookup"><span data-stu-id="cf544-151">*Out of support*</span></span>           |              |                             |              | <span data-ttu-id="cf544-152">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-152">Ships in-box</span></span> |              |
| <span data-ttu-id="cf544-153">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="cf544-153">Windows Server 2008 R2 SP1</span></span>              | <span data-ttu-id="cf544-154">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-154">Yes</span></span>          | <span data-ttu-id="cf544-155">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-155">Yes</span></span>                         | <span data-ttu-id="cf544-156">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-156">Yes</span></span>          | <span data-ttu-id="cf544-157">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-157">Yes</span></span>          | <span data-ttu-id="cf544-158">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-158">Ships in-box</span></span> |
| <span data-ttu-id="cf544-159">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="cf544-159">Windows 7 SP1</span></span>                           | <span data-ttu-id="cf544-160">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-160">Yes</span></span>          | <span data-ttu-id="cf544-161">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-161">Yes</span></span>                         | <span data-ttu-id="cf544-162">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-162">Yes</span></span>          | <span data-ttu-id="cf544-163">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-163">Yes</span></span>          | <span data-ttu-id="cf544-164">Incluso</span><span class="sxs-lookup"><span data-stu-id="cf544-164">Ships in-box</span></span> |
| <span data-ttu-id="cf544-165">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="cf544-165">Windows Server 2008 SP2</span></span>                 |              |                             |              | <span data-ttu-id="cf544-166">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-166">Yes</span></span>          | <span data-ttu-id="cf544-167">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-167">Yes</span></span>          |
| <span data-ttu-id="cf544-168">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="cf544-168">Windows Vista</span></span><br><span data-ttu-id="cf544-169">*Supporto scaduto*</span><span class="sxs-lookup"><span data-stu-id="cf544-169">*Out of support*</span></span>       |              |                             |              |              | <span data-ttu-id="cf544-170">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-170">Yes</span></span>          |
| <span data-ttu-id="cf544-171">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="cf544-171">Windows Server 2003</span></span><br><span data-ttu-id="cf544-172">*Supporto scaduto*</span><span class="sxs-lookup"><span data-stu-id="cf544-172">*Out of support*</span></span> |              |                             |              |              | <span data-ttu-id="cf544-173">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-173">Yes</span></span>          |
| <span data-ttu-id="cf544-174">Windows XP</span><span class="sxs-lookup"><span data-stu-id="cf544-174">Windows XP</span></span><br><span data-ttu-id="cf544-175">*Supporto scaduto*</span><span class="sxs-lookup"><span data-stu-id="cf544-175">*Out of support*</span></span>          |              |                             |              | <span data-ttu-id="cf544-176">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-176">Yes</span></span>          | <span data-ttu-id="cf544-177">Sì</span><span class="sxs-lookup"><span data-stu-id="cf544-177">Yes</span></span>          |

- <span data-ttu-id="cf544-178">**Incluso**: le funzionalità della versione specificata di WMF sono state rilasciate nella versione indicata di Windows Client o di Windows Server.</span><span class="sxs-lookup"><span data-stu-id="cf544-178">**Ships in-box**: The features of the specified version of WMF were shipped in the indicated version of Windows client or Windows Server.</span></span>
- <span data-ttu-id="cf544-179">**Supporto scaduto**: questi prodotti non sono più supportati da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cf544-179">**Out of support**: These products are no longer supported by Microsoft.</span></span> <span data-ttu-id="cf544-180">È necessario eseguire l'aggiornamento a una nuova versione supportata.</span><span class="sxs-lookup"><span data-stu-id="cf544-180">You must upgrade to a new version that is supported.</span></span> <span data-ttu-id="cf544-181">Per altre informazioni, vedere la pagina [Criteri relativi al ciclo di vita Microsoft][].</span><span class="sxs-lookup"><span data-stu-id="cf544-181">For more information, see the [Microsoft Lifecycle Policy][] page.</span></span>

> [!NOTE]
> <span data-ttu-id="cf544-182">Il programma di installazione di WMF 5.0 non è più disponibile o supportato.</span><span class="sxs-lookup"><span data-stu-id="cf544-182">The installer for WMF 5.0 is no longer available or supported.</span></span> <span data-ttu-id="cf544-183">È stato sostituito da WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="cf544-183">It has been replaced by WMF 5.1.</span></span>

[Criteri relativi al ciclo di vita Microsoft]: https://support.microsoft.com/lifecycle
[Microsoft Lifecycle Policy]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download