# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="6dfaa-101">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="6dfaa-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="6dfaa-102">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="6dfaa-103">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="6dfaa-104">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="6dfaa-105">Installazione tramite Homebrew in macOS 10.12 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="6dfaa-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="6dfaa-106">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="6dfaa-107">Da una finestra del terminale digitare `brew` per eseguire Homebrew.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="6dfaa-108">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="6dfaa-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="6dfaa-109">Se Homebrew è stato installato in precedenza, è sempre buona norma eseguire 'brew update-reset' && 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="6dfaa-110">Le versioni precedenti di Homebrew usano il tap 'caskroom/cask', deprecato e migrato a 'homebrew/cask'.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="6dfaa-111">Per altre informazioni, vedere [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="6dfaa-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="6dfaa-112">Usare il comando 'brew tap' per elencare i tap correnti.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="6dfaa-113">Se viene visualizzato il tap ' caskroom/cask' è possibile usare 'brew update' per eseguire la migrazione dei tap in Homebrew.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="6dfaa-114">Dopo aver installato/aggiornato Homebrew, l'installazione di PowerShell è semplice.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="6dfaa-115">Per installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="6dfaa-116">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="6dfaa-117">Per uscire da PowerShell e tornare a bash, usare il comando 'exit'.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="6dfaa-118">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="6dfaa-119">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire e riavviare la shell di PowerShell per completare l'aggiornamento e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="6dfaa-120">Installazione dell'anteprima tramite Homebrew in macOS 10.12 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="6dfaa-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="6dfaa-121">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="6dfaa-122">Da una finestra del terminale digitare `brew` per eseguire Homebrew.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="6dfaa-123">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="6dfaa-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="6dfaa-124">Se Homebrew è stato installato in precedenza, è sempre buona norma eseguire 'brew update-reset' && 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="6dfaa-125">Eseguire quindi il comando tap sul repository `versions` casks per ottenere il pacchetto di anteprima:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="6dfaa-126">Per installare l'anteprima di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="6dfaa-127">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="6dfaa-128">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento dell'anteprima di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="6dfaa-129">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire e riavviare la shell di PowerShell per completare l'aggiornamento e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="6dfaa-130">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="6dfaa-130">Installation via Direct Download</span></span>

<span data-ttu-id="6dfaa-131">Scaricare il pacchetto PKG `powershell-6.0.2-osx.10.12-x64.pkg` dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="6dfaa-132">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="6dfaa-133">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="6dfaa-133">Binary Archives</span></span>

<span data-ttu-id="6dfaa-134">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme macOS e Linux per abilitano scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="6dfaa-135">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="6dfaa-135">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="6dfaa-136">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6dfaa-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="6dfaa-137">Se PowerShell è stato installato con Homebrew, disinstallarlo è semplice:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="6dfaa-138">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="6dfaa-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="6dfaa-139">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi][] in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="6dfaa-140">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-140">This is not necessary if you installed with Homebrew.</span></span>

[Percorsi]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="6dfaa-142">Percorsi</span><span class="sxs-lookup"><span data-stu-id="6dfaa-142">Paths</span></span>

* <span data-ttu-id="6dfaa-143">`$PSHOME` è `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="6dfaa-144">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="6dfaa-145">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="6dfaa-146">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6dfaa-147">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6dfaa-148">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="6dfaa-149">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="6dfaa-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="6dfaa-150">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="6dfaa-151">Di conseguenza, i profili specifici dell'host predefinito sono presenti in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="6dfaa-152">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="6dfaa-153">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="6dfaa-154">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.0.2/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="6dfaa-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6dfaa-155">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="6dfaa-155">Additional Resources</span></span>

* <span data-ttu-id="6dfaa-156">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="6dfaa-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="6dfaa-157">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="6dfaa-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="6dfaa-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="6dfaa-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
