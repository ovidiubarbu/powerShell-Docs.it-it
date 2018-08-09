---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587466"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="a6052-103">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="a6052-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="a6052-104">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a6052-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="a6052-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="a6052-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="a6052-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="a6052-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="a6052-107">Installazione tramite Homebrew in macOS 10.12 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="a6052-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="a6052-108">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="a6052-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="a6052-109">Da una finestra del terminale digitare `brew` per eseguire Homebrew.</span><span class="sxs-lookup"><span data-stu-id="a6052-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="a6052-110">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="a6052-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="a6052-111">Se Homebrew è stato installato in precedenza, è sempre buona norma eseguire 'brew update-reset' && 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="a6052-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="a6052-112">Le versioni precedenti di Homebrew usano il tap 'caskroom/cask', deprecato e migrato a 'homebrew/cask'.</span><span class="sxs-lookup"><span data-stu-id="a6052-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="a6052-113">Per altre informazioni, vedere [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="a6052-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="a6052-114">Usare il comando 'brew tap' per elencare i tap correnti.</span><span class="sxs-lookup"><span data-stu-id="a6052-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="a6052-115">Se viene visualizzato il tap ' caskroom/cask' è possibile usare 'brew update' per eseguire la migrazione dei tap in Homebrew.</span><span class="sxs-lookup"><span data-stu-id="a6052-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="a6052-116">Dopo aver installato/aggiornato Homebrew, l'installazione di PowerShell è semplice.</span><span class="sxs-lookup"><span data-stu-id="a6052-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="a6052-117">Per installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a6052-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="a6052-118">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="a6052-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="a6052-119">Per uscire da PowerShell e tornare a bash, usare il comando 'exit'.</span><span class="sxs-lookup"><span data-stu-id="a6052-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="a6052-120">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a6052-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="a6052-121">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire e riavviare la shell di PowerShell per completare l'aggiornamento e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="a6052-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="a6052-122">Installazione dell'anteprima tramite Homebrew in macOS 10.12 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="a6052-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="a6052-123">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="a6052-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="a6052-124">Da una finestra del terminale digitare `brew` per eseguire Homebrew.</span><span class="sxs-lookup"><span data-stu-id="a6052-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="a6052-125">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="a6052-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="a6052-126">Se Homebrew è stato installato in precedenza, è sempre buona norma eseguire 'brew update-reset' && 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="a6052-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="a6052-127">Eseguire quindi il comando tap sul repository `versions` casks per ottenere il pacchetto di anteprima:</span><span class="sxs-lookup"><span data-stu-id="a6052-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="a6052-128">Per installare l'anteprima di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a6052-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="a6052-129">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="a6052-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="a6052-130">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento dell'anteprima di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a6052-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="a6052-131">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire e riavviare la shell di PowerShell per completare l'aggiornamento e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="a6052-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="a6052-132">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="a6052-132">Installation via Direct Download</span></span>

<span data-ttu-id="a6052-133">Scaricare il pacchetto PKG `powershell-6.0.2-osx.10.12-x64.pkg` dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="a6052-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="a6052-134">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="a6052-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="a6052-135">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="a6052-135">Binary Archives</span></span>

<span data-ttu-id="a6052-136">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme macOS e Linux per abilitano scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="a6052-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="a6052-137">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="a6052-137">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="a6052-138">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a6052-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="a6052-139">Se PowerShell è stato installato con Homebrew, disinstallarlo è semplice:</span><span class="sxs-lookup"><span data-stu-id="a6052-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="a6052-140">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="a6052-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="a6052-141">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi][] in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="a6052-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="a6052-142">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="a6052-142">This is not necessary if you installed with Homebrew.</span></span>

[Percorsi]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="a6052-144">Percorsi</span><span class="sxs-lookup"><span data-stu-id="a6052-144">Paths</span></span>

* <span data-ttu-id="a6052-145">`$PSHOME` è `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="a6052-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="a6052-146">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a6052-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a6052-147">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a6052-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a6052-148">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a6052-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a6052-149">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a6052-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a6052-150">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="a6052-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a6052-151">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a6052-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a6052-152">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="a6052-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="a6052-153">Di conseguenza, i profili specifici dell'host predefinito sono presenti in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="a6052-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a6052-154">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="a6052-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="a6052-155">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="a6052-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="a6052-156">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.0.2/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="a6052-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a6052-157">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a6052-157">Additional Resources</span></span>

* <span data-ttu-id="a6052-158">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="a6052-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="a6052-159">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="a6052-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="a6052-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="a6052-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
