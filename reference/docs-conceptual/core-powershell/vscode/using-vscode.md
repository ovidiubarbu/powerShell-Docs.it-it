---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: f8e1e9af257037fc7bd74549e4197c9a1695e952
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587432"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="e5b30-103">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5b30-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="e5b30-104">Oltre a [PowerShell ISE][ise], PowerShell è ben supportata anche in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e5b30-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="e5b30-105">ISE non è supportata in PowerShell Core, mentre Visual Studio Core è supportato per PowerShell Core in tutte le piattaforme (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="e5b30-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="e5b30-106">È possibile usare Visual Studio Code con la versione 5 di PowerShell in Windows con Windows 10 o installando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per sistemi operativi Windows inferiori (ad esempio, Windows 8.1 e così via).</span><span class="sxs-lookup"><span data-stu-id="e5b30-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="e5b30-107">Prima di procedere con l'avvio, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="e5b30-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="e5b30-108">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere:</span><span class="sxs-lookup"><span data-stu-id="e5b30-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="e5b30-109">[Installazione di PowerShell Core in Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="e5b30-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="e5b30-110">[Installazione di PowerShell Core in macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="e5b30-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="e5b30-111">[Installazione di PowerShell Core in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="e5b30-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="e5b30-112">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="e5b30-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="e5b30-113">Modifiche con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="e5b30-114">1. Installazione di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="e5b30-115">**Linux**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="e5b30-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="e5b30-116">**macOS**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="e5b30-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="e5b30-117">In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="e5b30-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="e5b30-118">Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](http://brew.sh/) e quindi eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="e5b30-118">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="e5b30-119">VS Code ora può caricare l'estensione PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5b30-119">VS Code can now load the the PowerShell extension successfully.</span></span>

- <span data-ttu-id="e5b30-120">**Windows**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="e5b30-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="e5b30-121">2. Installazione dell'estensione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5b30-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="e5b30-122">Avviare l'app di Visual Studio Code per:</span><span class="sxs-lookup"><span data-stu-id="e5b30-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="e5b30-123">**Windows**: digitando `code` nella sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5b30-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="e5b30-124">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="e5b30-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="e5b30-125">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="e5b30-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="e5b30-126">Avviare **Quick Open** premendo **CTRL+P** (**CMD+P** su Mac).</span><span class="sxs-lookup"><span data-stu-id="e5b30-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="e5b30-127">In Quick Open digitare `ext install powershell` e fare clic su **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="e5b30-128">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="e5b30-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="e5b30-129">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e5b30-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="e5b30-130">Dovrebbe essere visualizzato un contenuto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="e5b30-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="e5b30-132">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5b30-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="e5b30-133">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="e5b30-134">Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-134">Click on **Reload**.</span></span>
- <span data-ttu-id="e5b30-135">Dopo aver ricaricato Visual Studio Code, è possibile procedere con la modifica.</span><span class="sxs-lookup"><span data-stu-id="e5b30-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="e5b30-136">Ad esempio, per creare un nuovo file, fare clic su **File->Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="e5b30-137">Per salvarlo, fare clic su **File->Salva** e quindi specificare un nome per il file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e5b30-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="e5b30-138">Per chiudere il file, fare clic sulla "x" accanto al nome del file.</span><span class="sxs-lookup"><span data-stu-id="e5b30-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="e5b30-139">Per uscire da Visual Studio Code, **File->Esci**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="e5b30-140">Uso di una versione specifica di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5b30-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="e5b30-141">Se si vuole usare un'installazione specifica di PowerShell con Visual Studio Code, è necessario aggiungere una nuova variabile al file delle impostazioni utente.</span><span class="sxs-lookup"><span data-stu-id="e5b30-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="e5b30-142">Fare clic su **File -> Preferenze -> Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="e5b30-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="e5b30-143">Nell'editor verranno visualizzati due riquadri.</span><span class="sxs-lookup"><span data-stu-id="e5b30-143">Two editor panes appear.</span></span>
   <span data-ttu-id="e5b30-144">Nel riquadro di destra (`settings.json`) inserire la seguente impostazione, appropriata per il sistema operativo in uso, tra parentesi graffe (`{` e `}`) e sostituire **\<version\>** con la versione di PowerShell installata:</span><span class="sxs-lookup"><span data-stu-id="e5b30-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="e5b30-145">Sostituire l'impostazione con il percorso PowerShell desiderato eseguibile</span><span class="sxs-lookup"><span data-stu-id="e5b30-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="e5b30-146">Salvare il file di impostazioni e riavviare Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="e5b30-147">Impostazioni di configurazione per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="e5b30-148">Seguendo i passaggi descritti nel paragrafo precedente è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="e5b30-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="e5b30-149">Per Visual Studio Code, è consigliabile usare le impostazioni di configurazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="e5b30-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="e5b30-150">Debug con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="e5b30-151">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="e5b30-151">No-workspace debugging</span></span>

<span data-ttu-id="e5b30-152">A partire dalla versione 1.9 di Visual Studio Code, è possibile eseguire il debug degli script di PowerShell senza dover aprire la cartella contenente lo script in questione.</span><span class="sxs-lookup"><span data-stu-id="e5b30-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="e5b30-153">È sufficiente aprire il file di script di PowerShell tramite **File->Apri File...** , impostare un punto di interruzione su una riga (premere F9) e quindi premere F5 per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="e5b30-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="e5b30-154">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="e5b30-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="e5b30-155">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="e5b30-155">Workspace debugging</span></span>

<span data-ttu-id="e5b30-156">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code tramite **Apri cartella...**  dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="e5b30-157">La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="e5b30-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="e5b30-158">Anche con questa modalità, è possibile avviare il debug dello script selezionato di PowerShell premendo F5.</span><span class="sxs-lookup"><span data-stu-id="e5b30-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="e5b30-159">Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="e5b30-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="e5b30-160">Ad esempio, è possibile aggiungere una configurazione per:</span><span class="sxs-lookup"><span data-stu-id="e5b30-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="e5b30-161">avviare test di Pester nel debugger</span><span class="sxs-lookup"><span data-stu-id="e5b30-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="e5b30-162">avviare un file specifico con gli argomenti nel debugger</span><span class="sxs-lookup"><span data-stu-id="e5b30-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="e5b30-163">avviare una sessione interattiva nel debugger</span><span class="sxs-lookup"><span data-stu-id="e5b30-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="e5b30-164">collegare il debugger a un processo host di PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5b30-164">Attach the debugger to a PowerShell host process</span></span>

  <span data-ttu-id="e5b30-165">Seguire questi passaggi per creare il file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="e5b30-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="e5b30-166">Aprire la vista **Debug** premendo **CTRL+MAIUSC+D** (**CMD+MAIUSC+D** su Mac).</span><span class="sxs-lookup"><span data-stu-id="e5b30-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="e5b30-167">Premere l'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="e5b30-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="e5b30-168">Visual Studio Code richiederà di **selezionare l'ambiente**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-168">Visual Studio Code prompts you to **Select Environment**.</span></span>
  <span data-ttu-id="e5b30-169">Scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="e5b30-170">Quando si esegue questa operazione, Visual Studio Code crea una directory e un file ".vscode\launch.json" nella radice della cartella dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="e5b30-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="e5b30-171">Qui è archiviata la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="e5b30-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="e5b30-172">Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file launch.json.</span><span class="sxs-lookup"><span data-stu-id="e5b30-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="e5b30-173">I contenuti del file launch.json sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="e5b30-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="e5b30-174">Rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="e5b30-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="e5b30-175">Tuttavia quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="e5b30-176">Premere questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5b30-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="e5b30-177">Una configurazione utile da aggiungere è **PowerShell: avvia Script**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="e5b30-178">Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme F5, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="e5b30-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="e5b30-179">Una volta stabilita la configurazione di debug, è possibile selezionare la configurazione da usare durante una sessione di debug selezionandone una dal menu a discesa relativo alla configurazione nella visualizzazione della barra degli strumenti **Debug**.</span><span class="sxs-lookup"><span data-stu-id="e5b30-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

  <span data-ttu-id="e5b30-180">Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="e5b30-181">Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="e5b30-181">Visual Studio Code:</span></span>

- <span data-ttu-id="e5b30-182">[Estensione PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="e5b30-182">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="e5b30-183">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="e5b30-183">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="e5b30-184">[Indicazioni sul debug con Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="e5b30-184">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="e5b30-185">[Debug di PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="e5b30-185">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="e5b30-186">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="e5b30-186">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="e5b30-187">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="e5b30-187">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="e5b30-188">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="e5b30-188">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="e5b30-189">[Debug di script di PowerShell in Visual Studio Code – Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="e5b30-189">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="e5b30-190">[Debug di script di PowerShell in Visual Studio Code – Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="e5b30-190">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="e5b30-191">Estensione di PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5b30-191">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="e5b30-192">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="e5b30-192">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>