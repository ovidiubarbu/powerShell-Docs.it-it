---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 5251094388f6abc7da7f2cc706537eade78df7c9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978696"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="2e2d1-103">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e2d1-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="2e2d1-104">[Visual Studio Code][vscode] è un editor di script multipiattaforma di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-104">[Visual Studio Code][vscode] is a cross-platform script editor by Microsoft.</span></span> <span data-ttu-id="2e2d1-105">Insieme all'[estensione PowerShell][psext], offre un'esperienza di modifica degli script avanzata e interattiva, che semplifica la scrittura di script PowerShell affidabili.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-105">Together with the [PowerShell extension][psext], it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span> <span data-ttu-id="2e2d1-106">Visual Studio Code con l'estensione PowerShell è l'editor consigliato per la scrittura di script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>

<span data-ttu-id="2e2d1-107">Supporta le versioni di PowerShell seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="2e2d1-108">PowerShell 7 e versioni successive (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="2e2d1-108">PowerShell 7 and up (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="2e2d1-109">PowerShell Core 6 (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="2e2d1-109">PowerShell Core 6 (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="2e2d1-110">Windows PowerShell 5.1 (solo Windows)</span><span class="sxs-lookup"><span data-stu-id="2e2d1-110">Windows PowerShell 5.1 (Windows-only)</span></span>

> [!NOTE]
> <span data-ttu-id="2e2d1-111">Visual Studio Code non è [Visual Studio][].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-111">Visual Studio Code is not the same as [Visual Studio][].</span></span>

## <a name="getting-started"></a><span data-ttu-id="2e2d1-112">Introduzione</span><span class="sxs-lookup"><span data-stu-id="2e2d1-112">Getting started</span></span>

<span data-ttu-id="2e2d1-113">Prima di iniziare, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-113">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="2e2d1-114">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-114">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="2e2d1-115">[Installazione di PowerShell in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-115">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="2e2d1-116">[Installazione di PowerShell in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-116">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="2e2d1-117">[Installazione di PowerShell in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-117">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="2e2d1-118">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-118">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e2d1-119">[Windows PowerShell ISE][ise] continua a essere disponibile per Windows.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-119">The [Windows PowerShell ISE][ise] is still available for Windows.</span></span> <span data-ttu-id="2e2d1-120">Tuttavia, non viene più sviluppato in modo attivo.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-120">However, it is no longer in active feature development.</span></span> <span data-ttu-id="2e2d1-121">ISE non funziona con PowerShell 6 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-121">The ISE does not work with PowerShell 6 and higher.</span></span> <span data-ttu-id="2e2d1-122">Poiché è un componente di Windows, continua a essere supportato per la sicurezza e per le correzioni a priorità elevata.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-122">As a component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="2e2d1-123">Non è prevista la rimozione di ISE da Windows.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-123">We have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="2e2d1-124">Modifiche con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2e2d1-124">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="2e2d1-125">Installare Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-125">Install Visual Studio Code.</span></span> <span data-ttu-id="2e2d1-126">Per altre informazioni, vedere la panoramica [onfigurazione di Visual Studio Code][vsc-setup].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-126">For more information, see the overview [Setting up Visual Studio Code][vsc-setup].</span></span>

   <span data-ttu-id="2e2d1-127">Sono disponibili istruzioni per l'installazione per ogni piattaforma:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-127">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="2e2d1-128">**Windows**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Windows][vsc-setup-win].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-128">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows][vsc-setup-win] page.</span></span>
   - <span data-ttu-id="2e2d1-129">**macOS**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in macOS][vsc-setup-macOS].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-129">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS][vsc-setup-macOS] page.</span></span>
   - <span data-ttu-id="2e2d1-130">**Linux**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Linux][vsc-setup-linux].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-130">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux][vsc-setup-linux] page.</span></span>

1. <span data-ttu-id="2e2d1-131">Installare l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-131">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="2e2d1-132">Avviare l'app Visual Studio Code digitando `code` in una console o `code-insiders` se è stato installato Visual Studio Code Insider.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-132">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="2e2d1-133">Avviare **Quick Open** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-133">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="2e2d1-134">In macOS premere <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-134">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="2e2d1-135">Aprire Quick Open, digitare `ext install powershell`, quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-135">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="2e2d1-136">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-136">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="2e2d1-137">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-137">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="2e2d1-138">Verrà visualizzata una schermata Visual Studio Code simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-138">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="2e2d1-140">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-140">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="2e2d1-141">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**. Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-141">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="2e2d1-142">Dopo aver ricaricato Visual Studio Code, è possibile procedere con le operazioni di modifica.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-142">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="2e2d1-143">Per creare ad esempio un nuovo file, fare clic su **File > Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-143">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="2e2d1-144">Per salvarlo, fare clic su **File > Salva**, quindi specificare un nome file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-144">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="2e2d1-145">Per chiudere il file, fare clic sulla `X` accanto al nome file.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-145">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="2e2d1-146">Per uscire da Visual Studio Code, **File > Esci**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-146">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="2e2d1-147">Installare l'estensione di PowerShell in sistemi con restrizioni</span><span class="sxs-lookup"><span data-stu-id="2e2d1-147">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="2e2d1-148">Alcuni sistemi sono configurati in modo da richiedere la convalida di tutte le firme del codice.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-148">Some systems are set up to require validation of all code signatures.</span></span> <span data-ttu-id="2e2d1-149">È possibile che venga visualizzato l'errore seguente:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-149">You may receive the following error:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="2e2d1-150">Questo problema può verificarsi quando i criteri di esecuzione di PowerShell vengono impostati da Criteri di gruppo di Windows.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-150">This problem can occur when PowerShell's execution policy is set by Windows Group Policy.</span></span> <span data-ttu-id="2e2d1-151">Per approvare manualmente i servizi dell'editor PowerShell e l'estensione PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-151">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="2e2d1-152">Viene visualizzata la richiesta **Eseguire software di questo autore non attendibile?**</span><span class="sxs-lookup"><span data-stu-id="2e2d1-152">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="2e2d1-153">Digitare `A` per eseguire il file.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-153">Type `A` to run the file.</span></span> <span data-ttu-id="2e2d1-154">Aprire quindi Visual Studio Code e verificare che l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-154">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="2e2d1-155">Se i problemi persistono, segnalarlo su [Problemi di GitHub][].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-155">If you still have problems getting started, let us know on [GitHub issues][].</span></span>

> [!NOTE]
> <span data-ttu-id="2e2d1-156">L'estensione PowerShell per Visual Studio Code non supporta l'esecuzione in modalità di linguaggio vincolato.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-156">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="2e2d1-157">Per altre informazioni, vedere il [problema 606 su GitHub][i606].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-157">For more information, see [GitHub issue #606][i606].</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="2e2d1-158">Scelta di una versione di PowerShell da usare con l'estensione</span><span class="sxs-lookup"><span data-stu-id="2e2d1-158">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="2e2d1-159">Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una versione specifica di PowerShell con l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-159">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a specific version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="2e2d1-160">Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare le installazioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-160">This feature looks at a few well-known paths on different operating systems to discover installations of PowerShell.</span></span>

<span data-ttu-id="2e2d1-161">Attenersi alla procedura per scegliere la versione:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-161">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="2e2d1-162">Aprire il **riquadro comandi** in Windows o Linux con <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-162">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="2e2d1-163">In macOS usare <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-163">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="2e2d1-164">Cercare **Session** (Sessione).</span><span class="sxs-lookup"><span data-stu-id="2e2d1-164">Search for **Session**.</span></span>
1. <span data-ttu-id="2e2d1-165">Fare clic su **PowerShell: Show Session Menu** (Mostra menu sessione).</span><span class="sxs-lookup"><span data-stu-id="2e2d1-165">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="2e2d1-166">Scegliere la versione di PowerShell da usare dall'elenco, ad esempio: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-166">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

<span data-ttu-id="2e2d1-167">Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-167">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="2e2d1-168">È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-168">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

> [!NOTE]
> <span data-ttu-id="2e2d1-169">È anche possibile accedere al menu della sessione di PowerShell dal numero di versione verde nell'angolo inferiore destro della barra di stato.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-169">The PowerShell session menu can also be accessed from the green version number in the bottom right corner of status bar.</span></span> <span data-ttu-id="2e2d1-170">Facendo clic su questo numero di versione si apre il menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-170">Clicking this version number opens the session menu.</span></span>

## <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="2e2d1-171">Impostazioni di configurazione per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2e2d1-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="2e2d1-172">Se non si ha familiarità con le modalità di modifica delle impostazioni in Visual Studio Code, è consigliabile prima di tutto leggere [la documentazione sulle impostazioni di Visual Studio Code][vsc-settings].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-172">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend reading [Visual Studio Code's settings][vsc-settings] documentation.</span></span>

<span data-ttu-id="2e2d1-173">Dopo aver letto la documentazione, è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-173">After reading the documentation, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="2e2d1-174">Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, Visual Studio Code consente anche di definire configurazioni diverse per linguaggio.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-174">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="2e2d1-175">Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-175">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="2e2d1-176">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-176">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="2e2d1-177">Per altre informazioni sulla codifica dei file in Visual Studio Code, vedere [Informazioni sulla codifica di file][file-encoding].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-177">For more information about file encoding in Visual Studio Code, see [Understanding file encoding][file-encoding].</span></span>
>
> <span data-ttu-id="2e2d1-178">Per altri suggerimenti su come configurare Visual Studio Code per la modifica di PowerShell, vedere anche [Come replicare l'esperienza di ISE in Visual Studio Code][vsc-ise].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-178">Also, check out [How to replicate the ISE experience in Visual Studio Code][vsc-ise] for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="2e2d1-179">Aggiunta di percorsi di PowerShell personalizzati al menu della sessione</span><span class="sxs-lookup"><span data-stu-id="2e2d1-179">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="2e2d1-180">È possibile aggiungere altri percorsi dell'eseguibile PowerShell al menu della sessione tramite l'[impostazione di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-180">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="2e2d1-181">Aggiungere un elemento all'elenco `powershell.powerShellAdditionalExePaths` o creare l'elenco se non esiste nel file `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-181">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="2e2d1-182">Ogni elemento deve avere:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-182">Each item must have:</span></span>

- <span data-ttu-id="2e2d1-183">`exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-183">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="2e2d1-184">`versionName`: testo che verrà visualizzato nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-184">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="2e2d1-185">Per impostare la versione predefinita di PowerShell, impostare il valore `powershell.powerShellDefaultVersion` sul testo visualizzato nel menu della sessione (detto anche `versionName`):</span><span class="sxs-lookup"><span data-stu-id="2e2d1-185">To set the default PowerShell version, set the value `powershell.powerShellDefaultVersion` to the text displayed in the session menu (also known as the `versionName`):</span></span>

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

<span data-ttu-id="2e2d1-186">Dopo aver configurato questa impostazione, riavviare Visual Studio Code oppure per ricaricare la finestra di Visual Studio Code corrente dal  **riquadro comandi**, digitare **Sviluppatore: Ricarica finestra**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-186">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="2e2d1-187">Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-187">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="2e2d1-188">Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-188">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="2e2d1-189">Uso di una versione precedente dell'estensione PowerShell per Windows PowerShell V3 e V4</span><span class="sxs-lookup"><span data-stu-id="2e2d1-189">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="2e2d1-190">L'estensione PowerShell corrente non supporta [PowerShell V3 e V4][i1310].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-190">The current PowerShell extension doesn't support [PowerShell v3 and v4][i1310].</span></span> <span data-ttu-id="2e2d1-191">Tuttavia, è possibile usare la versione più recente dell'estensione che supporta PowerShell V3 e V4.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-191">However, you can use the last version of the extension that supports PowerShell v3 and v4.</span></span>

> [!CAUTION]
> <span data-ttu-id="2e2d1-192">Non verranno apportate correzioni aggiuntive a questa precedente versione dell'estensione.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-192">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="2e2d1-193">È disponibile nella configurazione attuale e solo se si usano ancora Windows PowerShell V3 e Windows PowerShell V4.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-193">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="2e2d1-194">In primo luogo aprire il riquadro Extension (Estensione) e cercare `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-194">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="2e2d1-195">Fare quindi clic sull'ingranaggio e selezionare **Install another version...** (Installa un'altra versione...).</span><span class="sxs-lookup"><span data-stu-id="2e2d1-195">Then click the gear and select **Install another version...**.</span></span>

![Installa un'altra versione...](media/using-vscode/install-another-version.png)

<span data-ttu-id="2e2d1-197">Selezionare quindi la versione **2020.1.0**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-197">Then select the **2020.1.0** version.</span></span> <span data-ttu-id="2e2d1-198">Questa è l'ultima versione dell'estensione che supporta V3 e V4.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-198">This version of the extension was the last version to support v3 and v4.</span></span> <span data-ttu-id="2e2d1-199">Assicurarsi di aggiungere l'impostazione seguente in modo che la versione dell'estensione non venga aggiornata automaticamente:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-199">Be sure to add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="2e2d1-200">La versione **2020.1.0** funzionerà nel prossimo futuro,</span><span class="sxs-lookup"><span data-stu-id="2e2d1-200">Version **2020.1.0** will work for the foreseeable future.</span></span> <span data-ttu-id="2e2d1-201">tuttavia, Visual Studio Code potrebbe implementare una modifica che interrompe questa versione dell'estensione.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-201">However, Visual Studio Code could implement a change that breaks this version of the extension.</span></span> <span data-ttu-id="2e2d1-202">Per questo motivo e per la mancanza di supporto, è consigliabile:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-202">Because of this, and lack of support, we recommend:</span></span>

- <span data-ttu-id="2e2d1-203">Aggiornare Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="2e2d1-203">Upgrading to Windows PowerShell 5.1</span></span>
- <span data-ttu-id="2e2d1-204">Installare PowerShell 7, vale a dire un'installazione affiancata di Windows PowerShell che funziona perfettamente con l'estensione PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e2d1-204">Install PowerShell 7, which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="2e2d1-205">Debug con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2e2d1-205">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="2e2d1-206">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="2e2d1-206">No-workspace debugging</span></span>

<span data-ttu-id="2e2d1-207">In Visual Studio Code 1.9 o versione successiva, è possibile eseguire il debug degli script di PowerShell senza aprire la cartella contenente lo script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-207">In Visual Studio Code version 1.9 (or higher), you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span>

1. <span data-ttu-id="2e2d1-208">Aprire il file di script di PowerShell con **File > Apri file...**</span><span class="sxs-lookup"><span data-stu-id="2e2d1-208">Open the PowerShell script file with **File > Open File...**</span></span>
1. <span data-ttu-id="2e2d1-209">Impostare un punto di interruzione, selezionare una riga, quindi premere <kbd>F9</kbd></span><span class="sxs-lookup"><span data-stu-id="2e2d1-209">Set a breakpoint - select a line then press <kbd>F9</kbd></span></span>
1. <span data-ttu-id="2e2d1-210">Premere <kbd>F5</kbd> per avviare il debug</span><span class="sxs-lookup"><span data-stu-id="2e2d1-210">Press <kbd>F5</kbd> to start debugging</span></span>

<span data-ttu-id="2e2d1-211">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-211">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="2e2d1-212">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="2e2d1-212">Workspace debugging</span></span>

<span data-ttu-id="2e2d1-213">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta dal menu **File** usando **Apri cartella**. La cartella che si apre si trova in genere nella cartella del progetto PowerShell o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-213">Workspace debugging refers to debugging in the context of a folder that you've opened from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder or the root of your Git repository.</span></span> <span data-ttu-id="2e2d1-214">Il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-214">Workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>

<span data-ttu-id="2e2d1-215">Seguire questi passaggi per creare un file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-215">Follow these steps to create a debug configuration file:</span></span>

1. <span data-ttu-id="2e2d1-216">Aprire la visualizzazione **Debug** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-216">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="2e2d1-217">In macOS premere <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-217">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
1. <span data-ttu-id="2e2d1-218">Fare clic sul collegamento per **creare un file launch.json**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-218">Click the **create a launch.json file** link.</span></span>
1. <span data-ttu-id="2e2d1-219">In **Seleziona ambiente** scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-219">From the **Select Environment** prompt, choose **PowerShell**.</span></span>
1. <span data-ttu-id="2e2d1-220">Scegliere il tipo di debug che si vuole usare:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-220">Choose the type of debugging you'd like to use:</span></span>

   - <span data-ttu-id="2e2d1-221">**Avviare il file corrente**: avviare ed eseguire il debug del file nella finestra dell'editor attualmente attiva</span><span class="sxs-lookup"><span data-stu-id="2e2d1-221">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
   - <span data-ttu-id="2e2d1-222">**Avviare lo script**: avviare ed eseguire il debug del file o del comando specificato</span><span class="sxs-lookup"><span data-stu-id="2e2d1-222">**Launch Script** - Launch and debug the specified file or command</span></span>
   - <span data-ttu-id="2e2d1-223">**Sessione interattiva**: eseguire il debug dei comandi eseguiti dalla console integrata</span><span class="sxs-lookup"><span data-stu-id="2e2d1-223">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
   - <span data-ttu-id="2e2d1-224">**Attach** (Associa): collegare il debugger a un processo host di PowerShell in esecuzione</span><span class="sxs-lookup"><span data-stu-id="2e2d1-224">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="2e2d1-225">Visual Studio Code crea una directory e un file `.vscode\launch.json` nella radice della cartella dell'area di lavoro per archiviare la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-225">Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder to store the debug configuration.</span></span> <span data-ttu-id="2e2d1-226">Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-226">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="2e2d1-227">Il contenuto del file `launch.json` è il seguente:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-227">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="2e2d1-228">Il file rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-228">This file represents the common debug scenarios.</span></span> <span data-ttu-id="2e2d1-229">Quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** .</span><span class="sxs-lookup"><span data-stu-id="2e2d1-229">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="2e2d1-230">È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-230">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="2e2d1-231">Una configurazione utile da aggiungere è **PowerShell: avvia script**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-231">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="2e2d1-232">Con questa configurazione, è possibile specificare un file contenente gli argomenti facoltativi che vengono usati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-232">With this configuration, you can specify a file containing optional arguments that are used whenever you press <kbd>F5</kbd> no matter which file is active in the editor.</span></span>

<span data-ttu-id="2e2d1-233">Dopo aver definito la configurazione di debug, è possibile selezionare la configurazione che si vuole usare durante una sessione di debug.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-233">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="2e2d1-234">Selezionare una configurazione dall'elenco a discesa delle configurazioni di debug nella barra degli strumenti della visualizzazione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-234">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="2e2d1-235">Risoluzione dei problemi dell'estensione PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2e2d1-235">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="2e2d1-236">Se si verificano problemi con Visual Studio Code durante lo sviluppo di script di PowerShell, vedere la [guida alla risoluzione dei problemi][troubleshooting] su GitHub.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-236">If you experience any issues using Visual Studio Code for PowerShell script development, see the [troubleshooting guide][troubleshooting] on GitHub.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="2e2d1-237">Risorse utili</span><span class="sxs-lookup"><span data-stu-id="2e2d1-237">Useful resources</span></span>

<span data-ttu-id="2e2d1-238">Sono disponibili video e blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="2e2d1-238">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="2e2d1-239">Video</span><span class="sxs-lookup"><span data-stu-id="2e2d1-239">Videos</span></span>

- [<span data-ttu-id="2e2d1-240">Usare Visual Studio Code come editor di PowerShell predefinito</span><span class="sxs-lookup"><span data-stu-id="2e2d1-240">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="2e2d1-241">Visual Studio Code: approfondimenti sul debug degli script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e2d1-241">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="2e2d1-242">Post di BLOG</span><span class="sxs-lookup"><span data-stu-id="2e2d1-242">Blog posts</span></span>

- <span data-ttu-id="2e2d1-243">[Estensione PowerShell][pscdn]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-243">[PowerShell Extension][pscdn]</span></span>
- <span data-ttu-id="2e2d1-244">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-244">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="2e2d1-245">[Indicazioni sul debug con Visual Studio Code][psdbgblog]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-245">[Debugging Visual Studio Code Guidance][psdbgblog]</span></span>
- <span data-ttu-id="2e2d1-246">[Debug di PowerShell in Visual Studio Code][psdbg-gh]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-246">[Debugging PowerShell in Visual Studio Code][psdbg-gh]</span></span>
- <span data-ttu-id="2e2d1-247">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-247">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="2e2d1-248">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-248">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="2e2d1-249">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-249">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="2e2d1-250">[Debug di script di PowerShell in Visual Studio Code - Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-250">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="2e2d1-251">[Debug di script di PowerShell in Visual Studio Code - Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="2e2d1-251">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-project-source-code"></a><span data-ttu-id="2e2d1-252">Codice sorgente del progetto di estensione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e2d1-252">PowerShell extension project source code</span></span>

<span data-ttu-id="2e2d1-253">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub][psext-src].</span><span class="sxs-lookup"><span data-stu-id="2e2d1-253">The PowerShell extension's source code can be found on [GitHub][psext-src].</span></span>

<span data-ttu-id="2e2d1-254">Per contribuire, è necessario usare le richieste pull.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-254">If you're interested in contributing, Pull Requests are greatly appreciated.</span></span> <span data-ttu-id="2e2d1-255">Per iniziare, seguire la [documentazione per gli sviluppatori][dev-docs] su GitHub.</span><span class="sxs-lookup"><span data-stu-id="2e2d1-255">Follow along with the [developer documentation][dev-docs] on GitHub to get started.</span></span>

<!-- related articles -->
[ise]:                    ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[Problemi di GitHub]:          https://github.com/PowerShell/vscode-powershell/issues
[GitHub issues]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
