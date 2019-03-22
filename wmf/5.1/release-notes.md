---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Note sulla versione di WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795012"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="813bd-103">Note sulla versione di Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="813bd-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span>

<span data-ttu-id="813bd-104">WMF 5.1 include i componenti PowerShell, WMI, WinRM e Registrazione inventario software (SIL) rilasciati con Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="813bd-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="813bd-105">WMF 5.1 può essere installato in Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e offre alcuni miglioramenti rispetto a WMF 5.0 RTM, tra cui:</span><span class="sxs-lookup"><span data-stu-id="813bd-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="813bd-106">Nuovi cmdlet: utenti locali e gruppi; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="813bd-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="813bd-107">I miglioramenti apportati a PowerShellGet includono l'applicazione di moduli firmati e l'installazione di moduli JEA</span><span class="sxs-lookup"><span data-stu-id="813bd-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="813bd-108">È stato aggiunto il supporto di PackageManagement per i contenitori, l'installazione di CBS, l'installazione basata su EXE e i pacchetti CAB</span><span class="sxs-lookup"><span data-stu-id="813bd-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="813bd-109">Miglioramenti del debug per le classi DSC e PowerShell</span><span class="sxs-lookup"><span data-stu-id="813bd-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="813bd-110">Miglioramenti relativi alla sicurezza, incluso quando si usano i cmdlet PowerShellGet e quando si applicano i moduli firmati da catalogo provenienti dal server di pull</span><span class="sxs-lookup"><span data-stu-id="813bd-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="813bd-111">Risposte ad alcune richieste o problemi segnalati da utenti</span><span class="sxs-lookup"><span data-stu-id="813bd-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="813bd-112">**Note importanti:**</span><span class="sxs-lookup"><span data-stu-id="813bd-112">**Important notes:**</span></span>

- <span data-ttu-id="813bd-113">**WMF 5.1 richiede .NET Framework 4.5.2** (o versione successiva).</span><span class="sxs-lookup"><span data-stu-id="813bd-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="813bd-114">Se .NET 4.5.2 (o versione successiva) non è disponibile, WMF verrà installato correttamente, ma le funzionalità principali non verranno eseguite.</span><span class="sxs-lookup"><span data-stu-id="813bd-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="813bd-115">Le istruzioni sono disponibili nell'argomento [Installare e configurare WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).</span><span class="sxs-lookup"><span data-stu-id="813bd-115">Instructions are available in the [Install and Configure WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="813bd-116">WMF 5.1 deve essere disinstallato prima dell'installazione WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="813bd-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="813bd-117">È possibile installare WMF 5.1 direttamente su WMF 5.0 o WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="813bd-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="813bd-118">__Non è necessario__ installare WMF 4.0 prima di installare WMF 5.1 in Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="813bd-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="813bd-119">Questo problema presente nella versione di WMF 5.1 (anteprima) è stato risolto.</span><span class="sxs-lookup"><span data-stu-id="813bd-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>
