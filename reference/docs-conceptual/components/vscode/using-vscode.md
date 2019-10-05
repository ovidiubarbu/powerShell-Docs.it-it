---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325240"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="abf36-103">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="abf36-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="abf36-104">Oltre a [PowerShell ISE][ise], PowerShell è supportato correttamente anche in Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="abf36-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="abf36-105">L'ambiente ISE non è supportato in PowerShell Core, mentre VSCode è supportato per PowerShell Core in tutte le piattaforme (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="abf36-105">Furthermore, the ISE is not supported with PowerShell Core, while VSCode is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="abf36-106">È possibile usare VSCode in Windows con la versione 5 di PowerShell con Windows 10 o installando [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) per sistemi operativi Windows inferiori (ad esempio, Windows 8.1 e così via).</span><span class="sxs-lookup"><span data-stu-id="abf36-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="abf36-107">Prima di procedere con l'avvio, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="abf36-107">Before starting it, please make sure PowerShell exists on your system.</span></span> <span data-ttu-id="abf36-108">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere:</span><span class="sxs-lookup"><span data-stu-id="abf36-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="abf36-109">[Installazione di PowerShell Core in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="abf36-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="abf36-110">[Installazione di PowerShell Core in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="abf36-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="abf36-111">[Installazione di PowerShell Core in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="abf36-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="abf36-112">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="abf36-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="abf36-113">Modifica con VSCode</span><span class="sxs-lookup"><span data-stu-id="abf36-113">Editing with VSCode</span></span>

1. [<span data-ttu-id="abf36-114">Installazione di VSCode</span><span class="sxs-lookup"><span data-stu-id="abf36-114">Installing VSCode</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

   - <span data-ttu-id="abf36-115">**Linux**: seguire le istruzioni di installazione nella pagina [Esecuzione di VSCode in Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="abf36-115">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>
   - <span data-ttu-id="abf36-116">**macOS**: seguire le istruzioni di installazione nella pagina [Esecuzione di VSCode in macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="abf36-116">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="abf36-117">In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="abf36-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="abf36-118">Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](https://brew.sh/) e quindi eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="abf36-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="abf36-119">VSCode può ora caricare l'estensione PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf36-119">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="abf36-120">**Windows**: seguire le istruzioni di installazione nella pagina [Esecuzione di VSCode in Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="abf36-120">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

2. <span data-ttu-id="abf36-121">Installazione dell'estensione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="abf36-121">Installing PowerShell Extension</span></span>

   - <span data-ttu-id="abf36-122">Avviare l'app VSCode come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="abf36-122">Launch the VSCode app by:</span></span>
     - <span data-ttu-id="abf36-123">**Windows**: digitando `code` nella sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="abf36-123">**Windows**: typing `code` in your PowerShell session</span></span>
     - <span data-ttu-id="abf36-124">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="abf36-124">**Linux**: typing `code` in your terminal</span></span>
     - <span data-ttu-id="abf36-125">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="abf36-125">**macOS**: typing `code` in your terminal</span></span>
   - <span data-ttu-id="abf36-126">Avviare **Quick Open** premendo <kbd>CTRL</kbd>+<kbd>P</kbd> (<kbd>Comando</kbd>+<kbd>P</kbd> in Mac).</span><span class="sxs-lookup"><span data-stu-id="abf36-126">Launch **Quick Open** by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>P</kbd> on Mac).</span></span>
   - <span data-ttu-id="abf36-127">In Quick Open digitare `ext install powershell` e fare clic su **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="abf36-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
   - <span data-ttu-id="abf36-128">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="abf36-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="abf36-129">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="abf36-129">Select the PowerShell extension from Microsoft.</span></span>
     <span data-ttu-id="abf36-130">Dovrebbe essere visualizzato un contenuto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="abf36-130">You should see something like below:</span></span>

     ![VSCode](../../images/using-vscode/vscode.png)

   - <span data-ttu-id="abf36-132">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf36-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   - <span data-ttu-id="abf36-133">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**.</span><span class="sxs-lookup"><span data-stu-id="abf36-133">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="abf36-134">Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="abf36-134">Click on **Reload**.</span></span>
   - <span data-ttu-id="abf36-135">Dopo il ricaricamento di VSCode, si è pronti per la modifica.</span><span class="sxs-lookup"><span data-stu-id="abf36-135">After VSCode has reload, you are ready for editing.</span></span>

<span data-ttu-id="abf36-136">Ad esempio, per creare un nuovo file, fare clic su **File->Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="abf36-136">For example, to create a new file, click **File->New**.</span></span> <span data-ttu-id="abf36-137">Per salvarlo, fare clic su **File->Salva** e quindi specificare un nome per il file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="abf36-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span> <span data-ttu-id="abf36-138">Per chiudere il file, fare clic sulla "x" accanto al nome del file.</span><span class="sxs-lookup"><span data-stu-id="abf36-138">To close the file, click on "x" next to the file name.</span></span> <span data-ttu-id="abf36-139">Per uscire da VSCode, **File-> Esci**.</span><span class="sxs-lookup"><span data-stu-id="abf36-139">To exit VSCode, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="abf36-140">Installare l'estensione di PowerShell in sistemi con restrizioni</span><span class="sxs-lookup"><span data-stu-id="abf36-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="abf36-141">Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice e pertanto è richiesta l'approvazione manuale dei servizi dell'editor di PowerShell per poterli eseguire nel sistema.</span><span class="sxs-lookup"><span data-stu-id="abf36-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="abf36-142">Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una causa probabile se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="abf36-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="abf36-143">Per approvare manualmente i servizi dell'editor di PowerShell e quindi l'estensione di PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire:</span><span class="sxs-lookup"><span data-stu-id="abf36-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="abf36-144">Viene visualizzata la richiesta "Eseguire software di questo autore non attendibile?"</span><span class="sxs-lookup"><span data-stu-id="abf36-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span> <span data-ttu-id="abf36-145">Digitare `R` per eseguire il file.</span><span class="sxs-lookup"><span data-stu-id="abf36-145">Type `R` to run the file.</span></span> <span data-ttu-id="abf36-146">Aprire quindi VSCode e verificare che l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="abf36-146">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="abf36-147">Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="abf36-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="abf36-148">Scelta di una versione di PowerShell da usare con l'estensione</span><span class="sxs-lookup"><span data-stu-id="abf36-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="abf36-149">Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una particolare versione di PowerShell con l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf36-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="abf36-150">Usare questa procedura per scegliere la versione:</span><span class="sxs-lookup"><span data-stu-id="abf36-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="abf36-151">Aprire il riquadro comandi (<kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in Windows e Linux, <kbd>Comando</kbd> + <kbd>Maiuscole</kbd>+<kbd>P</kbd> in macOS).</span><span class="sxs-lookup"><span data-stu-id="abf36-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="abf36-152">Cercare "Session" (Sessione).</span><span class="sxs-lookup"><span data-stu-id="abf36-152">Search for "Session".</span></span>
1. <span data-ttu-id="abf36-153">Fare clic su "PowerShell: Show Session Menu" (Mostra menu sessione).</span><span class="sxs-lookup"><span data-stu-id="abf36-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="abf36-154">Scegliere la versione di PowerShell da usare dall'elenco, ad esempio, "PowerShell Core".</span><span class="sxs-lookup"><span data-stu-id="abf36-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abf36-155">Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare i percorsi di installazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf36-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="abf36-156">Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="abf36-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="abf36-157">È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="abf36-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="abf36-158">Esiste un altro modo per accedere al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="abf36-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="abf36-159">Quando un file di PowerShell è aperto nell'editor, viene visualizzato un numero di versione verde in basso a destra.</span><span class="sxs-lookup"><span data-stu-id="abf36-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="abf36-160">Facendo clic su questo numero di versione si passerà al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="abf36-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="abf36-161">Aggiunta di percorsi di PowerShell personalizzati al menu della sessione</span><span class="sxs-lookup"><span data-stu-id="abf36-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="abf36-162">È possibile aggiungere altri percorsi per l'eseguibile di PowerShell al menu della sessione tramite un'impostazione di VSCode.</span><span class="sxs-lookup"><span data-stu-id="abf36-162">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="abf36-163">Aggiungere un elemento all'elenco `powershell.powerShellAdditionalExePaths` o creare l'elenco se non esiste nel file `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="abf36-163">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="abf36-164">Ogni elemento deve avere:</span><span class="sxs-lookup"><span data-stu-id="abf36-164">Each item must have:</span></span>

* <span data-ttu-id="abf36-165">`exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="abf36-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="abf36-166">`versionName`: testo che verrà visualizzato nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="abf36-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="abf36-167">È possibile impostare la versione di PowerShell predefinita da usare con l'impostazione `powershell.powerShellDefaultVersion`, specificando il testo visualizzato nel menu della sessione (ovvero `versionName` nell'ultima impostazione):</span><span class="sxs-lookup"><span data-stu-id="abf36-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="abf36-168">Dopo aver specificato questa impostazione, riavviare VSCode o usare l'azione del riquadro comandi "Sviluppatore: Ricarica finestra" per ricaricare la finestra di VSCode corrente.</span><span class="sxs-lookup"><span data-stu-id="abf36-168">Once you've set this setting, restart VSCode or use the the "Developer: Reload Window" command pallet action to reload the current VSCode window.</span></span>

<span data-ttu-id="abf36-169">Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.</span><span class="sxs-lookup"><span data-stu-id="abf36-169">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="abf36-170">Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf36-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="abf36-171">Impostazioni di configurazione per VSCode</span><span class="sxs-lookup"><span data-stu-id="abf36-171">Configuration settings for VSCode</span></span>

<span data-ttu-id="abf36-172">Seguendo i passaggi descritti nel paragrafo precedente è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="abf36-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="abf36-173">È consigliabile usare le impostazioni di configurazione seguenti per VSCode:</span><span class="sxs-lookup"><span data-stu-id="abf36-173">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="abf36-174">Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, VS Code consente anche di definire configurazioni diverse in base al linguaggio.</span><span class="sxs-lookup"><span data-stu-id="abf36-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="abf36-175">Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="abf36-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="abf36-176">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="abf36-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="abf36-177">Per altre informazioni sulla codifica dei file in VSCode, vedere [Informazioni sulla codifica di file](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="abf36-177">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="abf36-178">Debug con VSCode</span><span class="sxs-lookup"><span data-stu-id="abf36-178">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="abf36-179">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="abf36-179">No-workspace debugging</span></span>

<span data-ttu-id="abf36-180">A partire dalla versione 1.9 di VSCode, è possibile eseguire il debug degli script di PowerShell senza dover aprire la cartella contenente lo script in questione.</span><span class="sxs-lookup"><span data-stu-id="abf36-180">As of VSCode version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="abf36-181">Aprire il file di script di PowerShell tramite **File->Apri File**, impostare un punto di interruzione su una riga (premere <kbd>F9</kbd>) e quindi premere <kbd>F5</kbd> per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="abf36-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press <kbd>F9</kbd>) and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="abf36-182">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="abf36-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="abf36-183">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="abf36-183">Workspace debugging</span></span>

<span data-ttu-id="abf36-184">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code tramite **Apri cartella...**  dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="abf36-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span> <span data-ttu-id="abf36-185">La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="abf36-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="abf36-186">Anche con questa modalità, è possibile avviare il debug dello script selezionato di PowerShell premendo <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="abf36-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="abf36-187">Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="abf36-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="abf36-188">Ad esempio, è possibile aggiungere una configurazione per:</span><span class="sxs-lookup"><span data-stu-id="abf36-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="abf36-189">avviare test di Pester nel debugger</span><span class="sxs-lookup"><span data-stu-id="abf36-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="abf36-190">avviare un file specifico con gli argomenti nel debugger</span><span class="sxs-lookup"><span data-stu-id="abf36-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="abf36-191">avviare una sessione interattiva nel debugger</span><span class="sxs-lookup"><span data-stu-id="abf36-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="abf36-192">collegare il debugger a un processo host di PowerShell</span><span class="sxs-lookup"><span data-stu-id="abf36-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="abf36-193">Seguire questi passaggi per creare il file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="abf36-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="abf36-194">Aprire la visualizzazione **Debug** premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd> (<kbd>Comando</kbd>+<kbd>Maiuscole</kbd>+<kbd>D</kbd> in Mac).</span><span class="sxs-lookup"><span data-stu-id="abf36-194">Open the **Debug** view by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> on Mac).</span></span>
  2. <span data-ttu-id="abf36-195">Fare clic sull'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="abf36-195">Click the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="abf36-196">VSCode richiederà di **selezionare l'ambiente**.</span><span class="sxs-lookup"><span data-stu-id="abf36-196">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="abf36-197">Scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="abf36-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="abf36-198">Quando si esegue questa operazione, VSCode crea una directory e un file ".vscode\launch.json" nella radice della cartella dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="abf36-198">When you do this, VSCode creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span> <span data-ttu-id="abf36-199">Qui è archiviata la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="abf36-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="abf36-200">Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file launch.json.</span><span class="sxs-lookup"><span data-stu-id="abf36-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span> <span data-ttu-id="abf36-201">I contenuti del file launch.json sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="abf36-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="abf36-202">Rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="abf36-202">This represents the common debug scenarios.</span></span> <span data-ttu-id="abf36-203">Tuttavia quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** .</span><span class="sxs-lookup"><span data-stu-id="abf36-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="abf36-204">È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abf36-204">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="abf36-205">Una configurazione utile da aggiungere è **PowerShell: avvia script**.</span><span class="sxs-lookup"><span data-stu-id="abf36-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="abf36-206">Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="abf36-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="abf36-207">Una volta stabilita la configurazione di debug, è possibile selezionare la configurazione da usare durante una sessione di debug selezionandone una dal menu a discesa relativo alla configurazione nella visualizzazione della barra degli strumenti **Debug**.</span><span class="sxs-lookup"><span data-stu-id="abf36-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="abf36-208">Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="abf36-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="abf36-209">[Estensione PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="abf36-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="abf36-210">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="abf36-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="abf36-211">[Indicazioni sul debug con Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="abf36-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="abf36-212">[Debug di PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="abf36-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="abf36-213">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="abf36-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="abf36-214">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="abf36-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="abf36-215">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="abf36-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="abf36-216">[Debug di script di PowerShell in Visual Studio Code - Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="abf36-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="abf36-217">[Debug di script di PowerShell in Visual Studio Code - Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="abf36-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="abf36-218">Estensione di PowerShell per VSCode</span><span class="sxs-lookup"><span data-stu-id="abf36-218">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="abf36-219">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="abf36-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
