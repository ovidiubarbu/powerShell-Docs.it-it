---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082417"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="69625-103">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="69625-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="69625-104">[Visual Studio Code](https://code.visualstudio.com/) è un editor di script multipiattaforma (Windows, macOS e Linux) fornito da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69625-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="69625-105">Insieme all'[estensione PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), offre un'esperienza di modifica degli script avanzata e interattiva, che semplifica la scrittura di script PowerShell affidabili.</span><span class="sxs-lookup"><span data-stu-id="69625-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="69625-106">Visual Studio Code con l'estensione PowerShell è l'editor consigliato per la scrittura di script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="69625-107">Supporta le versioni di PowerShell seguenti:</span><span class="sxs-lookup"><span data-stu-id="69625-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="69625-108">PowerShell 7 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="69625-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="69625-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="69625-109">PowerShell Core 6</span></span>
- <span data-ttu-id="69625-110">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="69625-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="69625-111">Prima di iniziare, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="69625-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="69625-112">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="69625-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="69625-113">[Installazione di PowerShell Core in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="69625-113">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="69625-114">[Installazione di PowerShell Core in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="69625-114">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="69625-115">[Installazione di PowerShell Core in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="69625-115">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="69625-116">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="69625-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="69625-117">Visual Studio Code non è [Visual Studio](https://visualstudio.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="69625-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69625-118">[Windows PowerShell ISE][ise] è ancora disponibile per Windows, ma non è più incluso nello sviluppo delle funzionalità attive e non funziona con PowerShell 7 e versioni successive o con PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="69625-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="69625-119">Questo componente distribuito con Windows continua a essere supportato per la sicurezza e per le correzioni a priorità elevata.</span><span class="sxs-lookup"><span data-stu-id="69625-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="69625-120">Attualmente non è prevista la rimozione di ISE da Windows.</span><span class="sxs-lookup"><span data-stu-id="69625-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="69625-121">Modifiche con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69625-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="69625-122">Installare Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="69625-122">Install Visual Studio Code.</span></span> <span data-ttu-id="69625-123">Per altre informazioni, vedere la panoramica [onfigurazione di Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="69625-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="69625-124">Sono disponibili istruzioni per l'installazione per ogni piattaforma:</span><span class="sxs-lookup"><span data-stu-id="69625-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="69625-125">**Windows**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Windows](https://code.visualstudio.com/docs/setup/windows).</span><span class="sxs-lookup"><span data-stu-id="69625-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="69625-126">**macOS**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in macOS](https://code.visualstudio.com/docs/setup/mac).</span><span class="sxs-lookup"><span data-stu-id="69625-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="69625-127">**Linux**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Linux](https://code.visualstudio.com/docs/setup/linux).</span><span class="sxs-lookup"><span data-stu-id="69625-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="69625-128">Installare l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="69625-129">Avviare l'app Visual Studio Code digitando `code` in una console o `code-insiders` se è stato installato Visual Studio Code Insider.</span><span class="sxs-lookup"><span data-stu-id="69625-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="69625-130">Avviare **Quick Open** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="69625-131">In macOS premere <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="69625-132">Aprire Quick Open, digitare `ext install powershell`, quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="69625-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="69625-133">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="69625-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="69625-134">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69625-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="69625-135">Verrà visualizzata una schermata Visual Studio Code simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="69625-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="69625-137">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="69625-138">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**. Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="69625-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="69625-139">Dopo aver ricaricato Visual Studio Code, è possibile procedere con le operazioni di modifica.</span><span class="sxs-lookup"><span data-stu-id="69625-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="69625-140">Per creare ad esempio un nuovo file, fare clic su **File > Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="69625-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="69625-141">Per salvarlo, fare clic su **File > Salva**, quindi specificare un nome file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="69625-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="69625-142">Per chiudere il file, fare clic sulla `X` accanto al nome file.</span><span class="sxs-lookup"><span data-stu-id="69625-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="69625-143">Per uscire da Visual Studio Code, **File > Esci**.</span><span class="sxs-lookup"><span data-stu-id="69625-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="69625-144">Installare l'estensione di PowerShell in sistemi con restrizioni</span><span class="sxs-lookup"><span data-stu-id="69625-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="69625-145">Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice ed è richiesta l'approvazione manuale dei servizi dell'editor PowerShell per poterli eseguire nel sistema.</span><span class="sxs-lookup"><span data-stu-id="69625-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="69625-146">Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una possibile causa se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="69625-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="69625-147">Per approvare manualmente i servizi dell'editor PowerShell e l'estensione PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="69625-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="69625-148">Viene visualizzata la richiesta **Eseguire software di questo autore non attendibile?**</span><span class="sxs-lookup"><span data-stu-id="69625-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="69625-149">Digitare `A` per eseguire il file.</span><span class="sxs-lookup"><span data-stu-id="69625-149">Type `A` to run the file.</span></span> <span data-ttu-id="69625-150">Aprire quindi Visual Studio Code e verificare che l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="69625-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="69625-151">Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="69625-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="69625-152">L'estensione PowerShell per Visual Studio Code non supporta l'esecuzione in modalità di linguaggio vincolato.</span><span class="sxs-lookup"><span data-stu-id="69625-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="69625-153">Per altre informazioni, vedere la [gestione dei problemi GitHub supportati](https://github.com/PowerShell/vscode-powershell/issues/606).</span><span class="sxs-lookup"><span data-stu-id="69625-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="69625-154">Uso di una versione precedente dell'estensione PowerShell per Windows PowerShell V3 e V4</span><span class="sxs-lookup"><span data-stu-id="69625-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="69625-155">Anche se l'estensione PowerShell corrente [non supporta più le versioni 3 e 4](https://github.com/PowerShell/vscode-powershell/issues/1310), è comunque possibile usare la versione più recente dell'estensione che supportava queste versioni.</span><span class="sxs-lookup"><span data-stu-id="69625-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="69625-156">Non verranno apportate correzioni aggiuntive a questa precedente versione dell'estensione.</span><span class="sxs-lookup"><span data-stu-id="69625-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="69625-157">È disponibile nella configurazione attuale e solo se si usano ancora Windows PowerShell V3 e Windows PowerShell V4.</span><span class="sxs-lookup"><span data-stu-id="69625-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="69625-158">In primo luogo aprire il riquadro Extension (Estensione) e cercare `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="69625-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="69625-159">Fare quindi clic sull'ingranaggio e selezionare **Install another version...** (Installa un'altra versione...).</span><span class="sxs-lookup"><span data-stu-id="69625-159">Then click the gear and select **Install another version...**.</span></span>

![Installa un'altra versione...](media/using-vscode/install-another-version.png)

<span data-ttu-id="69625-161">Selezionare quindi la versione **`2020.1.0`** .</span><span class="sxs-lookup"><span data-stu-id="69625-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="69625-162">Questa è l'ultima versione dell'estensione che supporta V3 e V4.</span><span class="sxs-lookup"><span data-stu-id="69625-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="69625-163">Aggiungere anche l'impostazione seguente in modo che la versione dell'estensione non venga aggiornata automaticamente:</span><span class="sxs-lookup"><span data-stu-id="69625-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="69625-164">Sebbene funzionerà in un prossimo futuro, Visual Studio Code potrebbe implementare una modifica che interrompe questa versione dell'estensione.</span><span class="sxs-lookup"><span data-stu-id="69625-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="69625-165">Per questo motivo e per la mancanza di supporto, è consigliabile eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="69625-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="69625-166">Scaricare PowerShell 7, vale a dire un'installazione affiancata di Windows PowerShell che funziona perfettamente con l'estensione PowerShell</span><span class="sxs-lookup"><span data-stu-id="69625-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="69625-167">Aggiornare Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="69625-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="69625-168">La sezione [Modifiche con Visual Studio Code](#editing-with-visual-studio-code) in questo articolo contiene i collegamenti per le installazioni.</span><span class="sxs-lookup"><span data-stu-id="69625-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="69625-169">Scelta di una versione di PowerShell da usare con l'estensione</span><span class="sxs-lookup"><span data-stu-id="69625-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="69625-170">Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una versione particolare di PowerShell con l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="69625-171">Attenersi alla procedura per scegliere la versione:</span><span class="sxs-lookup"><span data-stu-id="69625-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="69625-172">Aprire il **riquadro comandi** in Windows o Linux con <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="69625-173">In macOS usare <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="69625-174">Cercare **Session** (Sessione).</span><span class="sxs-lookup"><span data-stu-id="69625-174">Search for **Session**.</span></span>
1. <span data-ttu-id="69625-175">Fare clic su **PowerShell: Show Session Menu** (Mostra menu sessione).</span><span class="sxs-lookup"><span data-stu-id="69625-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="69625-176">Scegliere la versione di PowerShell da usare dall'elenco, ad esempio: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="69625-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69625-177">Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare i percorsi di installazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="69625-178">Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="69625-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="69625-179">È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="69625-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="69625-180">Esiste un altro modo per accedere al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="69625-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="69625-181">Quando un file di PowerShell è aperto nell'editor, viene visualizzato un numero di versione verde in basso a destra.</span><span class="sxs-lookup"><span data-stu-id="69625-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="69625-182">Facendo clic su questo numero di versione si passerà al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="69625-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="69625-183">Aggiunta di percorsi di PowerShell personalizzati al menu della sessione</span><span class="sxs-lookup"><span data-stu-id="69625-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="69625-184">È possibile aggiungere altri percorsi dell'eseguibile PowerShell al menu della sessione tramite l'[impostazione di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="69625-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="69625-185">Aggiungere un elemento all'elenco `powershell.powerShellAdditionalExePaths` o creare l'elenco se non esiste nel file `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="69625-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="69625-186">Ogni elemento deve avere:</span><span class="sxs-lookup"><span data-stu-id="69625-186">Each item must have:</span></span>

- <span data-ttu-id="69625-187">`exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="69625-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="69625-188">`versionName`: testo che verrà visualizzato nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="69625-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="69625-189">È possibile impostare la versione di PowerShell predefinita da usare con l'impostazione `powershell.powerShellDefaultVersion`, specificando il testo visualizzato nel menu della sessione, vale a dire `versionName` nell'ultima impostazione:</span><span class="sxs-lookup"><span data-stu-id="69625-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="69625-190">Dopo aver configurato questa impostazione, riavviare Visual Studio Code oppure per ricaricare la finestra di Visual Studio Code corrente dal  **riquadro comandi**, digitare **Sviluppatore: Ricarica finestra**.</span><span class="sxs-lookup"><span data-stu-id="69625-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="69625-191">Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.</span><span class="sxs-lookup"><span data-stu-id="69625-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="69625-192">Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="69625-193">Impostazioni di configurazione per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69625-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="69625-194">Se non si ha familiarità con le modalità di modifica delle impostazioni in Visual Studio Code, è consigliabile prima di tutto esaminare [la documentazione sulle impostazioni di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).</span><span class="sxs-lookup"><span data-stu-id="69625-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="69625-195">Seguendo la procedura descritta nel paragrafo precedente, è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="69625-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="69625-196">Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, Visual Studio Code consente anche di definire configurazioni diverse per linguaggio.</span><span class="sxs-lookup"><span data-stu-id="69625-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="69625-197">Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="69625-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="69625-198">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="69625-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="69625-199">Per altre informazioni sulla codifica dei file in Visual Studio Code, vedere [Informazioni sulla codifica di file](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="69625-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="69625-200">Per altri suggerimenti su come configurare Visual Studio Code per la modifica di PowerShell, vedere anche [Come replicare l'esperienza di ISE in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md).</span><span class="sxs-lookup"><span data-stu-id="69625-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="69625-201">Debug con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69625-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="69625-202">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="69625-202">No-workspace debugging</span></span>

<span data-ttu-id="69625-203">A partire dalla versione 1.9 di Visual Studio Code, è possibile eseguire il debug degli script di PowerShell senza aprire la cartella contenente lo script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="69625-204">Aprire il file di script di PowerShell tramite **File > Apri File**, impostare un punto di interruzione in una riga, premere <kbd>F9</kbd>, quindi premere <kbd>F5</kbd> per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="69625-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="69625-205">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="69625-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="69625-206">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="69625-206">Workspace debugging</span></span>

<span data-ttu-id="69625-207">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code dal menu **File** usando **Apri cartella**. La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="69625-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="69625-208">Anche con questa modalità, è possibile avviare il debug dello script di PowerShell attualmente selezionato premendo <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="69625-209">Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="69625-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="69625-210">Verranno analizzate più avanti.</span><span class="sxs-lookup"><span data-stu-id="69625-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="69625-211">Seguire questi passaggi per creare il file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="69625-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="69625-212">Aprire la visualizzazione **Debug** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="69625-213">In macOS premere <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="69625-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="69625-214">Fare clic sul collegamento per creare un file launch.json.</span><span class="sxs-lookup"><span data-stu-id="69625-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="69625-215">Visual Studio Code richiederà di **selezionare l'ambiente**.</span><span class="sxs-lookup"><span data-stu-id="69625-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="69625-216">Scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="69625-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="69625-217">Infine, scegliere il tipo di debug che si vuole usare:</span><span class="sxs-lookup"><span data-stu-id="69625-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="69625-218">**Avviare il file corrente**: avviare ed eseguire il debug del file nella finestra dell'editor attualmente attiva</span><span class="sxs-lookup"><span data-stu-id="69625-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="69625-219">**Avviare lo script**: avviare ed eseguire il debug del file o del comando specificato</span><span class="sxs-lookup"><span data-stu-id="69625-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="69625-220">**Sessione interattiva**: eseguire il debug dei comandi eseguiti dalla console integrata</span><span class="sxs-lookup"><span data-stu-id="69625-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="69625-221">**Collegare**: collegare il debugger a un processo host di PowerShell in esecuzione</span><span class="sxs-lookup"><span data-stu-id="69625-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="69625-222">Visual Studio Code creerà una directory e un file `.vscode\launch.json` nella radice della cartella dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="69625-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="69625-223">In questa posizione è archiviata la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="69625-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="69625-224">Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="69625-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="69625-225">Il contenuto del file `launch.json` è il seguente:</span><span class="sxs-lookup"><span data-stu-id="69625-225">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="69625-226">Il file rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="69625-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="69625-227">Quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** .</span><span class="sxs-lookup"><span data-stu-id="69625-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="69625-228">È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69625-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="69625-229">Una configurazione utile da aggiungere è **PowerShell: avvia script**.</span><span class="sxs-lookup"><span data-stu-id="69625-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="69625-230">Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="69625-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="69625-231">Dopo aver definito la configurazione di debug, è possibile selezionare la configurazione che si vuole usare durante una sessione di debug.</span><span class="sxs-lookup"><span data-stu-id="69625-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="69625-232">Selezionare una configurazione dall'elenco a discesa delle configurazioni di debug nella barra degli strumenti della visualizzazione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="69625-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="69625-233">Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="69625-233">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="69625-234">[Estensione PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="69625-234">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="69625-235">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="69625-235">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="69625-236">[Indicazioni sul debug con Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="69625-236">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="69625-237">[Debug di PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="69625-237">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="69625-238">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="69625-238">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="69625-239">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="69625-239">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="69625-240">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="69625-240">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="69625-241">[Debug di script di PowerShell in Visual Studio Code - Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="69625-241">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="69625-242">[Debug di script di PowerShell in Visual Studio Code - Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="69625-242">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="69625-243">Estensione di PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69625-243">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="69625-244">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="69625-244">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="69625-245">Per contribuire, le richieste pull sono molto apprezzate.</span><span class="sxs-lookup"><span data-stu-id="69625-245">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="69625-246">Per iniziare, seguire la [documentazione per gli sviluppatori su GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md).</span><span class="sxs-lookup"><span data-stu-id="69625-246">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="69625-247">Risoluzione dei problemi dell'estensione PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="69625-247">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="69625-248">Se si verificano problemi con Visual Studio Code durante lo sviluppo di script di PowerShell, vedere la [guida alla risoluzione dei problemi su GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="69625-248">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>
