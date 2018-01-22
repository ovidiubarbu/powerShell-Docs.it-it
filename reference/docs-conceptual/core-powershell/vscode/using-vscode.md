# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="86de7-101">Uso di Visual Studio Code per sviluppare PowerShell</span><span class="sxs-lookup"><span data-stu-id="86de7-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="86de7-102">Oltre a [PowerShell ISE][ise], PowerShell è ben supportata anche in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="86de7-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="86de7-103">ISE non è supportata in PowerShell Core, mentre Visual Studio Core è supportato per PowerShell Core in tutte le piattaforme (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="86de7-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="86de7-104">È possibile usare Visual Studio Code con la versione 5 di PowerShell in Windows con Windows 10 o installando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per sistemi operativi Windows inferiori (ad esempio, Windows 8.1 e così via).</span><span class="sxs-lookup"><span data-stu-id="86de7-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="86de7-105">Prima di procedere con l'avvio, verificare che PowerShell sia presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="86de7-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="86de7-106">Per carichi di lavoro moderni in Windows, macOS e Linux, vedere:</span><span class="sxs-lookup"><span data-stu-id="86de7-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="86de7-107">[Installazione di PowerShell Core in macOS e Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="86de7-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="86de7-108">[Installazione di PowerShell Core in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="86de7-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="86de7-109">Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="86de7-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="86de7-110">Modifiche con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="86de7-111">1. Installazione di Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="86de7-112">**Linux**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="86de7-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="86de7-113">**macOS**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su macOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="86de7-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86de7-114">In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="86de7-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="86de7-115">Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](http://brew.sh/) e quindi eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="86de7-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="86de7-116">A questo punto l'estensione di PowerShell sarà in grado di caricare correttamente.</span><span class="sxs-lookup"><span data-stu-id="86de7-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="86de7-117">**Windows**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="86de7-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="86de7-118">2. Installazione dell'estensione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86de7-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="86de7-119">Avviare l'app di Visual Studio Code per:</span><span class="sxs-lookup"><span data-stu-id="86de7-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="86de7-120">**Windows**: digitando `code` nella sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86de7-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="86de7-121">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="86de7-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="86de7-122">**Linux**: digitando `code` nel terminale</span><span class="sxs-lookup"><span data-stu-id="86de7-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="86de7-123">Avviare **Quick Open** premendo **CTRL+P** (**CMD+P** su Mac).</span><span class="sxs-lookup"><span data-stu-id="86de7-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="86de7-124">In Quick Open digitare `ext install powershell` e fare clic su **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="86de7-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="86de7-125">La vista **Estensioni** si aprirà nella barra laterale.</span><span class="sxs-lookup"><span data-stu-id="86de7-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="86de7-126">Selezionare l'estensione di PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86de7-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="86de7-127">Verranno visualizzate informazioni come:</span><span class="sxs-lookup"><span data-stu-id="86de7-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="86de7-129">Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86de7-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="86de7-130">Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**.</span><span class="sxs-lookup"><span data-stu-id="86de7-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="86de7-131">Fare clic su **Ricarica**.</span><span class="sxs-lookup"><span data-stu-id="86de7-131">Click on **Reload**.</span></span>
- <span data-ttu-id="86de7-132">Dopo aver ricaricato Visual Studio Code, è possibile procedere con la modifica.</span><span class="sxs-lookup"><span data-stu-id="86de7-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="86de7-133">Ad esempio, per creare un nuovo file, fare clic su **File->Nuovo**.</span><span class="sxs-lookup"><span data-stu-id="86de7-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="86de7-134">Per salvarlo, fare clic su **File->Salva** e quindi specificare un nome per il file, ad esempio `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="86de7-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="86de7-135">Per chiudere il file, fare clic sulla "x" accanto al nome del file.</span><span class="sxs-lookup"><span data-stu-id="86de7-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="86de7-136">Per uscire da Visual Studio Code, **File->Esci**.</span><span class="sxs-lookup"><span data-stu-id="86de7-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="86de7-137">Uso di una versione specifica di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86de7-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="86de7-138">Se si vuole usare un'installazione specifica di PowerShell con Visual Studio Code, è necessario aggiungere una nuova variabile per il file nelle impostazioni utente.</span><span class="sxs-lookup"><span data-stu-id="86de7-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="86de7-139">Fare clic su **File -> Preferenze -> Impostazioni**</span><span class="sxs-lookup"><span data-stu-id="86de7-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="86de7-140">Nell'editor verranno visualizzati due riquadri.</span><span class="sxs-lookup"><span data-stu-id="86de7-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="86de7-141">Nel riquadro di destra (`settings.json`) inserire la seguente impostazione, relativa al proprio sistema operativo, tra parentesi graffe (`{` e `}`) e sostituire *<version>* con la versione di PowerShell installata:</span><span class="sxs-lookup"><span data-stu-id="86de7-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="86de7-142">Sostituire l'impostazione con il percorso PowerShell desiderato eseguibile</span><span class="sxs-lookup"><span data-stu-id="86de7-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="86de7-143">Salvare il file di impostazioni e riavviare Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="86de7-144">Impostazioni di configurazione per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="86de7-145">Seguendo i passaggi descritti nel paragrafo precedente è possibile aggiungere le impostazioni di configurazione in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="86de7-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="86de7-146">Per Visual Studio Code, è consigliabile usare le impostazioni di configurazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="86de7-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="86de7-147">Debug con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="86de7-148">Debug senza area di lavoro</span><span class="sxs-lookup"><span data-stu-id="86de7-148">No-workspace debugging</span></span>

<span data-ttu-id="86de7-149">A partire dalla versione 1.9 di Visual Studio Code, è possibile eseguire il debug degli script di PowerShell senza dover aprire la cartella contenente lo script in questione.</span><span class="sxs-lookup"><span data-stu-id="86de7-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="86de7-150">È sufficiente aprire il file di script di PowerShell tramite **File->Apri File...** , impostare un punto di interruzione su una riga (premere F9) e quindi premere F5 per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="86de7-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="86de7-151">Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riavviare e arrestare il debug.</span><span class="sxs-lookup"><span data-stu-id="86de7-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="86de7-152">Debug dell'area di lavoro</span><span class="sxs-lookup"><span data-stu-id="86de7-152">Workspace debugging</span></span>

<span data-ttu-id="86de7-153">Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code tramite **Apri cartella...**  dal menu **File**.</span><span class="sxs-lookup"><span data-stu-id="86de7-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="86de7-154">La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.</span><span class="sxs-lookup"><span data-stu-id="86de7-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="86de7-155">Anche con questa modalità, è possibile avviare il debug dello script selezionato di PowerShell premendo F5.</span><span class="sxs-lookup"><span data-stu-id="86de7-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="86de7-156">Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.</span><span class="sxs-lookup"><span data-stu-id="86de7-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="86de7-157">Ad esempio, è possibile aggiungere una configurazione per:</span><span class="sxs-lookup"><span data-stu-id="86de7-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="86de7-158">avviare test di Pester nel debugger</span><span class="sxs-lookup"><span data-stu-id="86de7-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="86de7-159">avviare un file specifico con gli argomenti nel debugger</span><span class="sxs-lookup"><span data-stu-id="86de7-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="86de7-160">avviare una sessione interattiva nel debugger</span><span class="sxs-lookup"><span data-stu-id="86de7-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="86de7-161">collegare il debugger a un processo host di PowerShell</span><span class="sxs-lookup"><span data-stu-id="86de7-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="86de7-162">Seguire questi passaggi per creare il file di configurazione di debug:</span><span class="sxs-lookup"><span data-stu-id="86de7-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="86de7-163">Aprire la vista **Debug** premendo **CTRL+MAIUSC+D** (**CMD+MAIUSC+D** su Mac).</span><span class="sxs-lookup"><span data-stu-id="86de7-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="86de7-164">Premere l'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="86de7-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="86de7-165">Visual Studio Code richiederà di **selezionare l'ambiente**.</span><span class="sxs-lookup"><span data-stu-id="86de7-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="86de7-166">Scegliere **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="86de7-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="86de7-167">Quando si esegue questa operazione, Visual Studio Code crea una directory e un file ".vscode\launch.json" nella radice della cartella dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="86de7-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="86de7-168">Qui è archiviata la configurazione di debug.</span><span class="sxs-lookup"><span data-stu-id="86de7-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="86de7-169">Se i file si trovano in un repository Git, in genere si vuole salvare il file launch.json.</span><span class="sxs-lookup"><span data-stu-id="86de7-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="86de7-170">I contenuti del file launch.json sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="86de7-170">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="86de7-171">Rappresenta gli scenari di debug comuni.</span><span class="sxs-lookup"><span data-stu-id="86de7-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="86de7-172">Tuttavia quando si apre il file nell'editor, verrà visualizzato il pulsante **Aggiungi configurazione...**.</span><span class="sxs-lookup"><span data-stu-id="86de7-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="86de7-173">Premere questo pulsante per aggiungere altre configurazioni di debug per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86de7-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="86de7-174">Una configurazione utile da aggiungere è **PowerShell: avvia Script**.</span><span class="sxs-lookup"><span data-stu-id="86de7-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="86de7-175">Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme F5, a prescindere dal file attivo nell'editor.</span><span class="sxs-lookup"><span data-stu-id="86de7-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="86de7-176">Una volta stabilita la configurazione di debug, è possibile selezionare la configurazione da usare durante una sessione di debug selezionandone una dal menu a discesa relativo alla configurazione nella visualizzazione della barra degli strumenti **Debug**.</span><span class="sxs-lookup"><span data-stu-id="86de7-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="86de7-177">Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="86de7-178">Visual Studio Code: [estensione di PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="86de7-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="86de7-179">[Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="86de7-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="86de7-180">[Indicazioni sul debug con Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="86de7-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="86de7-181">[Debug di PowerShell in Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="86de7-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="86de7-182">[Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="86de7-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="86de7-183">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="86de7-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="86de7-184">[Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="86de7-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="86de7-185">[Debug di script di PowerShell in Visual Studio Code – Parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="86de7-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="86de7-186">[Debug di script di PowerShell in Visual Studio Code – Parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="86de7-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="86de7-187">Estensione di PowerShell per Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86de7-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="86de7-188">I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="86de7-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
