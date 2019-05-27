---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 5badffd49252e0d72ae2c20d3147ad4b1e92d5ed
ms.sourcegitcommit: cf1a281cce9f7239c440c90f8b2798d32a13778d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882565"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="f7b40-103">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7b40-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="f7b40-104">Oltre a [PowerShell ISE][ise], PowerShell è ben supportata anche in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f7b40-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="f7b40-105">ISE non è supportata in PowerShell Core, mentre Visual Studio Core è supportato per PowerShell Core in tutte le piattaforme (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="f7b40-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="f7b40-106">È possibile usare Visual Studio Code con la versione 5 di PowerShell in Windows con Windows 10 o installando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per sistemi operativi Windows inferiori (ad esempio, Windows 8.1 e così via).</span><span class="sxs-lookup"><span data-stu-id="f7b40-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="f7b40-107">Prima di procedere con l'avvio, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="f7b40-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="f7b40-108">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere:</span><span class="sxs-lookup"><span data-stu-id="f7b40-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="f7b40-109">[Installazione di PowerShell Core in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="f7b40-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="f7b40-110">[Installazione di PowerShell Core in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="f7b40-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="f7b40-111">[Installazione di PowerShell Core in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="f7b40-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="f7b40-112">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="f7b40-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="f7b40-113">Modifiche con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f7b40-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="f7b40-114">1. Installazione di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f7b40-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="f7b40-115">**Linux**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="f7b40-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="f7b40-116">**macOS**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="f7b40-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f7b40-117">In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="f7b40-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="f7b40-118">Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](https://brew.sh/) e quindi eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="f7b40-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="f7b40-119">VS Code può ora caricare l'estensione PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b40-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="f7b40-120">**Windows**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="f7b40-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="f7b40-121">2. Installazione dell'estensione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7b40-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="f7b40-122">Avviare l'app di Visual Studio Code per:</span><span class="sxs-lookup"><span data-stu-id="f7b40-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="f7b40-123">**Windows**: digitando `code` nella sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7b40-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="f7b40-124">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="f7b40-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="f7b40-125">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="f7b40-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="f7b40-126">Avviare **Quick Open** premendo **CTRL+P** (**CMD+P** su Mac).</span><span class="sxs-lookup"><span data-stu-id="f7b40-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="f7b40-127">In Quick Open digitare `ext install powershell` e fare clic su **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="f7b40-128">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="f7b40-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="f7b40-129">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f7b40-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="f7b40-130">Dovrebbe essere visualizzato un contenuto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f7b40-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="f7b40-132">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b40-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="f7b40-133">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="f7b40-134">Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-134">Click on **Reload**.</span></span>
- <span data-ttu-id="f7b40-135">Dopo aver ricaricato Visual Studio Code, è possibile procedere con la modifica.</span><span class="sxs-lookup"><span data-stu-id="f7b40-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="f7b40-136">Ad esempio, per creare un nuovo file, fare clic su **File->Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="f7b40-137">Per salvarlo, fare clic su **File->Salva** e quindi specificare un nome per il file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="f7b40-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="f7b40-138">Per chiudere il file, fare clic sulla "x" accanto al nome del file.</span><span class="sxs-lookup"><span data-stu-id="f7b40-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="f7b40-139">Per uscire da Visual Studio Code, **File->Esci**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="f7b40-140">Installare l'estensione di PowerShell in sistemi con restrizioni</span><span class="sxs-lookup"><span data-stu-id="f7b40-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="f7b40-141">Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice e pertanto è richiesta l'approvazione manuale dei servizi dell'editor di PowerShell per poterli eseguire nel sistema.</span><span class="sxs-lookup"><span data-stu-id="f7b40-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="f7b40-142">Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una causa probabile se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f7b40-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="f7b40-143">Per approvare manualmente i servizi dell'editor di PowerShell e quindi l'estensione di PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire:</span><span class="sxs-lookup"><span data-stu-id="f7b40-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="f7b40-144">Viene visualizzata la richiesta "Eseguire software di questo autore non attendibile?"</span><span class="sxs-lookup"><span data-stu-id="f7b40-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="f7b40-145">Digitare `R` per eseguire il file.</span><span class="sxs-lookup"><span data-stu-id="f7b40-145">Type `R` to run the file.</span></span> <span data-ttu-id="f7b40-146">Aprire quindi Visual Studio Code e verificare che l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="f7b40-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="f7b40-147">Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="f7b40-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="f7b40-148">Scelta di una versione di PowerShell da usare con l'estensione</span><span class="sxs-lookup"><span data-stu-id="f7b40-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="f7b40-149">Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una particolare versione di PowerShell con l'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b40-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="f7b40-150">Usare questa procedura per scegliere la versione:</span><span class="sxs-lookup"><span data-stu-id="f7b40-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="f7b40-151">Aprire il riquadro comandi (<kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in Windows e Linux, <kbd>Comando</kbd> + <kbd>Maiuscole</kbd>+<kbd>P</kbd> in macOS).</span><span class="sxs-lookup"><span data-stu-id="f7b40-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="f7b40-152">Cercare "Session" (Sessione).</span><span class="sxs-lookup"><span data-stu-id="f7b40-152">Search for "Session".</span></span>
1. <span data-ttu-id="f7b40-153">Fare clic su "PowerShell: Show Session Menu" (Mostra menu sessione).</span><span class="sxs-lookup"><span data-stu-id="f7b40-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="f7b40-154">Scegliere la versione di PowerShell da usare dall'elenco, ad esempio, "PowerShell Core".</span><span class="sxs-lookup"><span data-stu-id="f7b40-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f7b40-155">Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare i percorsi di installazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b40-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="f7b40-156">Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="f7b40-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="f7b40-157">È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="f7b40-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="f7b40-158">Esiste un altro modo per accedere al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="f7b40-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="f7b40-159">Quando un file di PowerShell è aperto nell'editor, viene visualizzato un numero di versione verde in basso a destra.</span><span class="sxs-lookup"><span data-stu-id="f7b40-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="f7b40-160">Facendo clic su questo numero di versione si passerà al menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="f7b40-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="f7b40-161">Aggiunta di percorsi di PowerShell personalizzati al menu della sessione</span><span class="sxs-lookup"><span data-stu-id="f7b40-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="f7b40-162">È possibile aggiungere altri percorsi per l'eseguibile di PowerShell al menu della sessione tramite un'impostazione di Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f7b40-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="f7b40-163">Aggiungere un elemento all'elenco `powershell.powerShellAdditionalExePaths` o creare l'elenco se non esiste nel file `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="f7b40-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="f7b40-164">Ogni elemento deve avere:</span><span class="sxs-lookup"><span data-stu-id="f7b40-164">Each item must have:</span></span>

* <span data-ttu-id="f7b40-165">`exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.</span><span class="sxs-lookup"><span data-stu-id="f7b40-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="f7b40-166">`versionName`: testo che verrà visualizzato nel menu della sessione.</span><span class="sxs-lookup"><span data-stu-id="f7b40-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="f7b40-167">È possibile impostare la versione di PowerShell predefinita da usare con l'impostazione `powershell.powerShellDefaultVersion`, specificando il testo visualizzato nel menu della sessione (ovvero `versionName` nell'ultima impostazione):</span><span class="sxs-lookup"><span data-stu-id="f7b40-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="f7b40-168">Dopo aver specificato questa impostazione, riavviare Visual Studio Code o usare l'azione del riquadro comandi "Sviluppatore: Ricarica finestra" per ricaricare la finestra di Visual Studio Code corrente.</span><span class="sxs-lookup"><span data-stu-id="f7b40-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="f7b40-169">Se si apre il menu della sessione, verranno ora visualizzate le versioni di PowerShell aggiunte.</span><span class="sxs-lookup"><span data-stu-id="f7b40-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="f7b40-170">Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b40-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="f7b40-171">Impostazioni di configurazione per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f7b40-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="f7b40-172">Seguendo i passaggi descritti nel paragrafo precedente è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="f7b40-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="f7b40-173">Per Visual Studio Code, è consigliabile usare le impostazioni di configurazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="f7b40-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="f7b40-174">Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, VS Code consente anche di definire configurazioni diverse in base al linguaggio.</span><span class="sxs-lookup"><span data-stu-id="f7b40-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="f7b40-175">Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="f7b40-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="f7b40-176">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f7b40-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="f7b40-177">Per altre informazioni sulla codifica dei file in Visual Studio Code, vedere [Informazioni sulla codifica di file](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="f7b40-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="f7b40-178">Debug con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f7b40-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="f7b40-179">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="f7b40-179">No-workspace debugging</span></span>

<span data-ttu-id="f7b40-180">A partire dalla versione 1.9 di Visual Studio Code, è possibile eseguire il debug degli script di PowerShell senza dover aprire la cartella contenente lo script in questione.</span><span class="sxs-lookup"><span data-stu-id="f7b40-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="f7b40-181">Aprire il file di script di PowerShell tramite **File->Apri File**, impostare un punto di interruzione su una riga (premere F9) e quindi premere F5 per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="f7b40-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="f7b40-182">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="f7b40-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="f7b40-183">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="f7b40-183">Workspace debugging</span></span>

<span data-ttu-id="f7b40-184">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code tramite **Apri cartella...**  dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="f7b40-185">La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="f7b40-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="f7b40-186">Anche con questa modalità, è possibile avviare il debug dello script selezionato di PowerShell premendo F5.</span><span class="sxs-lookup"><span data-stu-id="f7b40-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="f7b40-187">Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="f7b40-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="f7b40-188">Ad esempio, è possibile aggiungere una configurazione per:</span><span class="sxs-lookup"><span data-stu-id="f7b40-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="f7b40-189">avviare test di Pester nel debugger</span><span class="sxs-lookup"><span data-stu-id="f7b40-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="f7b40-190">avviare un file specifico con gli argomenti nel debugger</span><span class="sxs-lookup"><span data-stu-id="f7b40-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="f7b40-191">avviare una sessione interattiva nel debugger</span><span class="sxs-lookup"><span data-stu-id="f7b40-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="f7b40-192">collegare il debugger a un processo host di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7b40-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="f7b40-193">Seguire questi passaggi per creare il file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="f7b40-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="f7b40-194">Aprire la vista **Debug** premendo **CTRL+MAIUSC+D** (**CMD+MAIUSC+D** su Mac).</span><span class="sxs-lookup"><span data-stu-id="f7b40-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="f7b40-195">Premere l'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="f7b40-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="f7b40-196">Visual Studio Code richiederà di **selezionare l'ambiente**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="f7b40-197">Scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="f7b40-198">Quando si esegue questa operazione, Visual Studio Code crea una directory e un file ".vscode\launch.json" nella radice della cartella dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="f7b40-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="f7b40-199">Qui è archiviata la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="f7b40-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="f7b40-200">Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file launch.json.</span><span class="sxs-lookup"><span data-stu-id="f7b40-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="f7b40-201">I contenuti del file launch.json sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="f7b40-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="f7b40-202">Rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="f7b40-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="f7b40-203">Tuttavia quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="f7b40-204">Premere questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b40-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="f7b40-205">Una configurazione utile da aggiungere è **PowerShell: avvia script**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="f7b40-206">Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme F5, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="f7b40-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="f7b40-207">Una volta stabilita la configurazione di debug, è possibile selezionare la configurazione da usare durante una sessione di debug selezionandone una dal menu a discesa relativo alla configurazione nella visualizzazione della barra degli strumenti **Debug**.</span><span class="sxs-lookup"><span data-stu-id="f7b40-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="f7b40-208">Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="f7b40-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="f7b40-209">[Estensione PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="f7b40-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="f7b40-210">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="f7b40-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="f7b40-211">[Indicazioni sul debug con Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="f7b40-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="f7b40-212">[Debug di PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="f7b40-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="f7b40-213">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="f7b40-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="f7b40-214">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="f7b40-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="f7b40-215">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="f7b40-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="f7b40-216">[Debug di script di PowerShell in Visual Studio Code – Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="f7b40-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="f7b40-217">[Debug di script di PowerShell in Visual Studio Code – Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="f7b40-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="f7b40-218">Estensione di PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f7b40-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="f7b40-219">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="f7b40-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
