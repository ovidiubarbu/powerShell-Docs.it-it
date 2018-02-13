---
ms.date: 2017-08-09
keywords: PowerShell, cmdlet, download, installazione, configurazione, Windows 10, Windows 8.1, Windows 8.0, Windows 7
title: Installazione di Windows PowerShell
ms.openlocfilehash: ec8f09087a5c5f2e7ea6237faa01ea3f447ad1f3
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="97e27-103">Installazione di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="97e27-104">PowerShell viene installato per impostazione predefinita in tutte le versioni di Windows, a partire da Windows 7 SP1 e Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="97e27-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="97e27-105">Per installare **PowerShell 6** (beta) in computer Linux, macOS e Windows, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="97e27-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="97e27-106">Scaricare da [GitHub](https://github.com/powershell/powershell#get-powershell) la versione di PowerShell idonea al sistema operativo specifico e alla versione</span><span class="sxs-lookup"><span data-stu-id="97e27-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="97e27-107">Seguire le istruzioni di installazione</span><span class="sxs-lookup"><span data-stu-id="97e27-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="97e27-108">Linux</span><span class="sxs-lookup"><span data-stu-id="97e27-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="97e27-109">macOS</span><span class="sxs-lookup"><span data-stu-id="97e27-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md)
  - [<span data-ttu-id="97e27-110">Windows</span><span class="sxs-lookup"><span data-stu-id="97e27-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="97e27-111">PowerShell 6 è disponibile anche per Docker. Vedere le istruzioni relative all'[installazione di Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).</span><span class="sxs-lookup"><span data-stu-id="97e27-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="97e27-112">Ricerca di PowerShell in Windows 10, 8.1, 8.0 e 7</span><span class="sxs-lookup"><span data-stu-id="97e27-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="97e27-113">Trovare la console o l'ISE (Integrated Scripting Environment) di PowerShell in Windows può risultare difficile, perché la posizione varia a seconda della versione di Windows.</span><span class="sxs-lookup"><span data-stu-id="97e27-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="97e27-114">Le tabelle seguenti permettono di trovare PowerShell nella versione di Windows corrente.</span><span class="sxs-lookup"><span data-stu-id="97e27-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="97e27-115">Tutte le versioni elencate di seguito sono versioni originali, così come rilasciate, senza aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="97e27-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="97e27-116">Per la console</span><span class="sxs-lookup"><span data-stu-id="97e27-116">For Console</span></span>

<span data-ttu-id="97e27-117">Versione</span><span class="sxs-lookup"><span data-stu-id="97e27-117">Version</span></span> | <span data-ttu-id="97e27-118">Posizione</span><span class="sxs-lookup"><span data-stu-id="97e27-118">Location</span></span>
-- | --
<span data-ttu-id="97e27-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="97e27-119">Windows 10</span></span> | <span data-ttu-id="97e27-120">Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="97e27-121">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="97e27-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="97e27-122">Nella schermata Start iniziare a digitare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97e27-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="97e27-123">Per l'edizione desktop, fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="97e27-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="97e27-124">Windows 7 SP1</span></span> | <span data-ttu-id="97e27-125">Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell nella casella di ricerca</span><span class="sxs-lookup"><span data-stu-id="97e27-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="97e27-126">Per l'ISE</span><span class="sxs-lookup"><span data-stu-id="97e27-126">For ISE</span></span>

<span data-ttu-id="97e27-127">Versione</span><span class="sxs-lookup"><span data-stu-id="97e27-127">Version</span></span> | <span data-ttu-id="97e27-128">Posizione</span><span class="sxs-lookup"><span data-stu-id="97e27-128">Location</span></span>
-- | --
<span data-ttu-id="97e27-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="97e27-129">Windows 10</span></span> | <span data-ttu-id="97e27-130">Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare ISE</span><span class="sxs-lookup"><span data-stu-id="97e27-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="97e27-131">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="97e27-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="97e27-132">Nella schermata Start digitare **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="97e27-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="97e27-133">Per l'edizione desktop, fare clic sull'icona di Windows nell'angolo in basso a sinistra e digitare **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="97e27-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="97e27-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="97e27-134">Windows 7 SP1</span></span> | <span data-ttu-id="97e27-135">Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell nella casella di ricerca</span><span class="sxs-lookup"><span data-stu-id="97e27-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="97e27-136">Ricerca di PowerShell nelle versioni di Windows Server</span><span class="sxs-lookup"><span data-stu-id="97e27-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="97e27-137">A partire da Windows Server 2008 R2, è possibile installare il sistema operativo Windows senza l'interfaccia utente grafica (GUI).</span><span class="sxs-lookup"><span data-stu-id="97e27-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="97e27-138">Le edizioni di Windows Server senza interfaccia utente grafica sono dette **Core**, mentre le edizioni con l'interfaccia utente grafica sono dette **Desktop**.</span><span class="sxs-lookup"><span data-stu-id="97e27-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="97e27-139">Windows Server Core Edition</span><span class="sxs-lookup"><span data-stu-id="97e27-139">Windows Server Core editions</span></span>

<span data-ttu-id="97e27-140">In tutte le edizioni Core quando si accede al server viene visualizzata una finestra del prompt dei comandi di Windows.</span><span class="sxs-lookup"><span data-stu-id="97e27-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="97e27-141">Digitare `powershell` e premere **INVIO** per avviare PowerShell all'interno della sessione del prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="97e27-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="97e27-142">Digitare `exit` per terminare la sessione di PowerShell e tornare al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="97e27-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="97e27-143">Windows Server Desktop Edition</span><span class="sxs-lookup"><span data-stu-id="97e27-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="97e27-144">In tutte le edizioni desktop fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97e27-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="97e27-145">Vengono visualizzate sia le opzioni console che ISE.</span><span class="sxs-lookup"><span data-stu-id="97e27-145">You get both console and ISE options.</span></span>

<span data-ttu-id="97e27-146">L'unica eccezione è rappresentata dall'ISE in Windows Server 2008 R2 SP1. In questo caso occorre fare clic sull'icona di Windows nell'angolo in basso a sinistra e digitare PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="97e27-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="97e27-147">Come verificare la versione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="97e27-148">Per determinare la versione di PowerShell installata, avviare una console o l'ISE di PowerShell, digitare `$PSVersionTable` e premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="97e27-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="97e27-149">Aggiornamento di Windows PowerShell esistente</span><span class="sxs-lookup"><span data-stu-id="97e27-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="97e27-150">Il pacchetto di installazione di PowerShell viene fornito all'interno di un programma di installazione di WMF.</span><span class="sxs-lookup"><span data-stu-id="97e27-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="97e27-151">La versione del programma di installazione di WMF corrisponde alla versione di PowerShell. Non esiste un programma di installazione autonomo per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97e27-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="97e27-152">Per aggiornare la versione esistente di PowerShell in Windows, usare la tabella seguente per trovare il programma di installazione per la versione di PowerShell da aggiornare.</span><span class="sxs-lookup"><span data-stu-id="97e27-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="97e27-153">Windows</span><span class="sxs-lookup"><span data-stu-id="97e27-153">Windows</span></span> | <span data-ttu-id="97e27-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="97e27-154">PS 3.0</span></span> | <span data-ttu-id="97e27-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="97e27-155">PS 4.0</span></span> | <span data-ttu-id="97e27-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="97e27-156">PS 5.0</span></span> | <span data-ttu-id="97e27-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="97e27-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="97e27-158">Windows 10 (vedere la nota 1)</span><span class="sxs-lookup"><span data-stu-id="97e27-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="97e27-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="97e27-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="97e27-160">installato</span><span class="sxs-lookup"><span data-stu-id="97e27-160">installed</span></span>
<span data-ttu-id="97e27-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="97e27-161">Windows 8.1</span></span><br/><span data-ttu-id="97e27-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="97e27-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="97e27-163">installato</span><span class="sxs-lookup"><span data-stu-id="97e27-163">installed</span></span> | [<span data-ttu-id="97e27-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="97e27-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="97e27-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97e27-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="97e27-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="97e27-166">Windows 8</span></span><br/><span data-ttu-id="97e27-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="97e27-167">Windows Server 2012</span></span> | <span data-ttu-id="97e27-168">installato</span><span class="sxs-lookup"><span data-stu-id="97e27-168">installed</span></span> | [<span data-ttu-id="97e27-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="97e27-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="97e27-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="97e27-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="97e27-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97e27-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="97e27-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="97e27-172">Windows 7 SP1</span></span><br/><span data-ttu-id="97e27-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="97e27-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="97e27-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="97e27-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="97e27-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="97e27-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="97e27-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="97e27-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="97e27-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97e27-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="97e27-178">**Nota 1**:</span><span class="sxs-lookup"><span data-stu-id="97e27-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="97e27-179">Nella versione iniziale di Windows 10, con gli aggiornamenti automatici abilitati, PowerShell viene aggiornato dalla versione 5.0 alla versione 5.1.</span><span class="sxs-lookup"><span data-stu-id="97e27-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="97e27-180">Se la versione originale di Windows 10 non viene aggiornata tramite Aggiornamenti di Windows, la versione di PowerShell è la 5.0.</span><span class="sxs-lookup"><span data-stu-id="97e27-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="97e27-181">È necessario Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-181">Need Azure PowerShell</span></span>

<span data-ttu-id="97e27-182">Se si cerca **Azure PowerShell**, è possibile iniziare da [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure) (Panoramica di Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="97e27-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="97e27-183">In caso contrario, potrebbe essere interessante vedere [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps) (Installare e configurare Azure PowerShell)</span><span class="sxs-lookup"><span data-stu-id="97e27-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="97e27-184">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="97e27-184">See Also</span></span>

- [<span data-ttu-id="97e27-185">Requisiti di sistema di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="97e27-186">Avvio di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97e27-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
