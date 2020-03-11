---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 16ae228c0d169261b783366a730fd2d5d77d32d6
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279070"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="88d48-103">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="88d48-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="88d48-104">Oltre a [PowerShell ISE][ise], PowerShell è supportato correttamente anche in Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="88d48-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="88d48-105">L'ambiente ISE non è supportato in PowerShell Core, mentre VSCode è supportato per PowerShell Core in tutte le piattaforme: Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="88d48-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="88d48-106">È possibile usare VSCode in Windows con la versione 5 di PowerShell usando Windows 10 o installando Windows Management Framework 5.1 per versioni precedenti dei sistemi operativi Windows, ad esempio Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="88d48-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="88d48-107">Per altre informazioni, vedere [Installare e configurare WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span><span class="sxs-lookup"><span data-stu-id="88d48-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="88d48-108">Prima di iniziare, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="88d48-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="88d48-109">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="88d48-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="88d48-110">[Installazione di PowerShell Core in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="88d48-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="88d48-111">[Installazione di PowerShell Core in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="88d48-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="88d48-112">[Installazione di PowerShell Core in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="88d48-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="88d48-113">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="88d48-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="88d48-114">Modifica con VSCode</span><span class="sxs-lookup"><span data-stu-id="88d48-114">Editing with VSCode</span></span>

1. <span data-ttu-id="88d48-115">Installare VSCode.</span><span class="sxs-lookup"><span data-stu-id="88d48-115">Install VSCode.</span></span> <span data-ttu-id="88d48-116">Per altre informazioni, vedere la panoramica [onfigurazione di Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="88d48-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="88d48-117">Sono disponibili istruzioni per l'installazione per ogni piattaforma:</span><span class="sxs-lookup"><span data-stu-id="88d48-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="88d48-118">**Linux**: seguire le istruzioni per l'installazione nella pagina [Esecuzione di VSCode in Linux](https://code.visualstudio.com/docs/setup/linux).</span><span class="sxs-lookup"><span data-stu-id="88d48-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="88d48-119">**macOS**: seguire le istruzioni per l'installazione nella pagina [Esecuzione di VSCode in macOS](https://code.visualstudio.com/docs/setup/mac).</span><span class="sxs-lookup"><span data-stu-id="88d48-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="88d48-120">In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="88d48-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="88d48-121">Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](https://brew.sh/) e quindi eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="88d48-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="88d48-122">VSCode può ora caricare l'estensione PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="88d48-123">**Windows**: seguire le istruzioni per l'installazione nella pagina [Esecuzione di VSCode in Windows](https://code.visualstudio.com/docs/setup/windows).</span><span class="sxs-lookup"><span data-stu-id="88d48-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="88d48-124">Installare l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="88d48-125">Avviare l'app VSCode come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="88d48-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="88d48-126">**Windows**: digitando `code` nella sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="88d48-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="88d48-127">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="88d48-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="88d48-128">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="88d48-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="88d48-129">Avviare **Quick Open** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="88d48-130">In macOS premere <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="88d48-131">Aprire Quick Open, digitare `ext install powershell`, quindi premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="88d48-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="88d48-132">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="88d48-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="88d48-133">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="88d48-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="88d48-134">Verrà visualizzata una schermata VSCode simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="88d48-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](media/using-vscode/vscode.png)

   1. <span data-ttu-id="88d48-136">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="88d48-137">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**.</span><span class="sxs-lookup"><span data-stu-id="88d48-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="88d48-138">Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="88d48-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="88d48-139">Dopo aver ricaricato VSCode, è possibile apportare le modifiche.</span><span class="sxs-lookup"><span data-stu-id="88d48-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="88d48-140">Per creare ad esempio un nuovo file, fare clic su **File > Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="88d48-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="88d48-141">Per salvarlo, fare clic su **File > Salva**, quindi specificare un nome file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="88d48-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="88d48-142">Per chiudere il file, fare clic sulla `X` accanto al nome file.</span><span class="sxs-lookup"><span data-stu-id="88d48-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="88d48-143">Per uscire da VSCode, **File > Esci**.</span><span class="sxs-lookup"><span data-stu-id="88d48-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="88d48-144">Installare l'estensione di PowerShell in sistemi con restrizioni</span><span class="sxs-lookup"><span data-stu-id="88d48-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="88d48-145">Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice ed è richiesta l'approvazione manuale dei servizi dell'editor PowerShell per poterli eseguire nel sistema.</span><span class="sxs-lookup"><span data-stu-id="88d48-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="88d48-146">Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una possibile causa se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="88d48-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="88d48-147">Per approvare manualmente i servizi dell'editor PowerShell e l'estensione di PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="88d48-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="88d48-148">Viene visualizzata la richiesta **Eseguire software di questo autore non attendibile?**</span><span class="sxs-lookup"><span data-stu-id="88d48-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="88d48-149">Digitare `A` per eseguire il file.</span><span class="sxs-lookup"><span data-stu-id="88d48-149">Type `A` to run the file.</span></span> <span data-ttu-id="88d48-150">Aprire quindi VSCode e verificare che l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="88d48-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="88d48-151">Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="88d48-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="88d48-152">Scelta di una versione di PowerShell da usare con l'estensione</span><span class="sxs-lookup"><span data-stu-id="88d48-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="88d48-153">Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una versione particolare di PowerShell con l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="88d48-154">Attenersi alla procedura per scegliere la versione:</span><span class="sxs-lookup"><span data-stu-id="88d48-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="88d48-155">Aprire il **riquadro comandi** in Windows o Linux con <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="88d48-156">In macOS usare <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="88d48-157">Cercare **Session** (Sessione).</span><span class="sxs-lookup"><span data-stu-id="88d48-157">Search for **Session**.</span></span>
1. <span data-ttu-id="88d48-158">Fare clic su **PowerShell: Show Session Menu** (Mostra menu sessione).</span><span class="sxs-lookup"><span data-stu-id="88d48-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="88d48-159">Scegliere la versione di PowerShell da usare dall'elenco, ad esempio: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="88d48-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88d48-160">Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare i percorsi di installazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="88d48-161">Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="88d48-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="88d48-162">È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="88d48-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="88d48-163">Esiste un altro modo per accedere al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="88d48-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="88d48-164">Quando un file di PowerShell è aperto nell'editor, viene visualizzato un numero di versione verde in basso a destra.</span><span class="sxs-lookup"><span data-stu-id="88d48-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="88d48-165">Facendo clic su questo numero di versione si passerà al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="88d48-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="88d48-166">Aggiunta di percorsi di PowerShell personalizzati al menu della sessione</span><span class="sxs-lookup"><span data-stu-id="88d48-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="88d48-167">È possibile aggiungere altri percorsi per l'eseguibile di PowerShell al menu della sessione tramite un'impostazione di VSCode.</span><span class="sxs-lookup"><span data-stu-id="88d48-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="88d48-168">Aggiungere un elemento all'elenco `powershell.powerShellAdditionalExePaths` o creare l'elenco se non esiste nel file `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="88d48-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="88d48-169">Ogni elemento deve avere:</span><span class="sxs-lookup"><span data-stu-id="88d48-169">Each item must have:</span></span>

* <span data-ttu-id="88d48-170">`exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="88d48-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="88d48-171">`versionName`: testo che verrà visualizzato nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="88d48-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="88d48-172">È possibile impostare la versione di PowerShell predefinita da usare con l'impostazione `powershell.powerShellDefaultVersion`, specificando il testo visualizzato nel menu della sessione, vale a dire `versionName` nell'ultima impostazione:</span><span class="sxs-lookup"><span data-stu-id="88d48-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="88d48-173">Dopo aver configurato questa impostazione, riavviare VSCode oppure per ricaricare la finestra di VSCode corrente dal  **riquadro comandi**, digitare **Sviluppatore: Ricarica finestra**.</span><span class="sxs-lookup"><span data-stu-id="88d48-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="88d48-174">Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.</span><span class="sxs-lookup"><span data-stu-id="88d48-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="88d48-175">Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="88d48-176">Impostazioni di configurazione per VSCode</span><span class="sxs-lookup"><span data-stu-id="88d48-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="88d48-177">Seguendo la procedura descritta nel paragrafo precedente, è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="88d48-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="88d48-178">È consigliabile usare le impostazioni di configurazione seguenti per VSCode:</span><span class="sxs-lookup"><span data-stu-id="88d48-178">We recommend the following configuration settings for VSCode:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="88d48-179">Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, VS Code consente anche di definire configurazioni diverse in base al linguaggio.</span><span class="sxs-lookup"><span data-stu-id="88d48-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="88d48-180">Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="88d48-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="88d48-181">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="88d48-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="88d48-182">Per altre informazioni sulla codifica dei file in VSCode, vedere [Informazioni sulla codifica di file](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="88d48-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="88d48-183">Debug con VSCode</span><span class="sxs-lookup"><span data-stu-id="88d48-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="88d48-184">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="88d48-184">No-workspace debugging</span></span>

<span data-ttu-id="88d48-185">A partire dalla versione 1.9 di VSCode, è possibile eseguire il debug degli script di PowerShell senza aprire la cartella contenente lo script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="88d48-186">Aprire il file di script di PowerShell tramite **File > Apri File**, impostare un punto di interruzione in una riga, premere <kbd>F9</kbd>, quindi premere <kbd>F5</kbd> per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="88d48-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="88d48-187">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="88d48-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="88d48-188">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="88d48-188">Workspace debugging</span></span>

<span data-ttu-id="88d48-189">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code dal menu **File** usando **Apri cartella**. La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="88d48-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="88d48-190">Anche con questa modalità, è possibile avviare il debug dello script di PowerShell attualmente selezionato premendo <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="88d48-191">Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="88d48-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="88d48-192">È ad esempio possibile aggiungere una configurazione per eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="88d48-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="88d48-193">Avviare test di Pester nel debugger.</span><span class="sxs-lookup"><span data-stu-id="88d48-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="88d48-194">Avviare un file specifico con gli argomenti nel debugger.</span><span class="sxs-lookup"><span data-stu-id="88d48-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="88d48-195">Avviare una sessione interattiva nel debugger.</span><span class="sxs-lookup"><span data-stu-id="88d48-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="88d48-196">Collegare il debugger a un processo host di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="88d48-197">Seguire questi passaggi per creare il file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="88d48-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="88d48-198">Aprire la visualizzazione **Debug** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="88d48-199">In macOS premere <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88d48-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="88d48-200">Fare clic sull'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="88d48-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="88d48-201">VSCode richiederà di **selezionare l'ambiente**.</span><span class="sxs-lookup"><span data-stu-id="88d48-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="88d48-202">Scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="88d48-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="88d48-203">VSCode creerà una directory e un file `.vscode\launch.json` nella radice della cartella dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="88d48-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="88d48-204">In questa posizione è archiviata la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="88d48-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="88d48-205">Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file `launch.json`.</span><span class="sxs-lookup"><span data-stu-id="88d48-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="88d48-206">Il contenuto del file `launch.json` è il seguente:</span><span class="sxs-lookup"><span data-stu-id="88d48-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="88d48-207">Il file rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="88d48-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="88d48-208">Quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** .</span><span class="sxs-lookup"><span data-stu-id="88d48-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="88d48-209">È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88d48-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="88d48-210">Una configurazione utile da aggiungere è **PowerShell: avvia script**.</span><span class="sxs-lookup"><span data-stu-id="88d48-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="88d48-211">Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="88d48-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="88d48-212">Dopo aver definito la configurazione di debug, è possibile selezionare la configurazione che si vuole usare durante una sessione di debug.</span><span class="sxs-lookup"><span data-stu-id="88d48-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="88d48-213">Selezionare una configurazione dall'elenco a discesa delle configurazioni di debug nella barra degli strumenti della visualizzazione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="88d48-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="88d48-214">Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="88d48-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="88d48-215">[Estensione PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="88d48-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="88d48-216">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="88d48-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="88d48-217">[Indicazioni sul debug con Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="88d48-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="88d48-218">[Debug di PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="88d48-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="88d48-219">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="88d48-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="88d48-220">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="88d48-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="88d48-221">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="88d48-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="88d48-222">[Debug di script di PowerShell in Visual Studio Code - Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="88d48-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="88d48-223">[Debug di script di PowerShell in Visual Studio Code - Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="88d48-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="88d48-224">Estensione di PowerShell per VSCode</span><span class="sxs-lookup"><span data-stu-id="88d48-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="88d48-225">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="88d48-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
